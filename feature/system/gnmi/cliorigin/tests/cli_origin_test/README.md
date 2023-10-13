# gNMI-1.1: cli Origin

## Summary

Ensure that emergency CLI configuration can be pushed to device.

## Procedure

Note: this test is intended to cover only the case of pushing some
configuration - since it is unknown what CLI configuration would be required in
the emergency case that is covered by this requirement.

*   Connect ATE port-1 to DUT port-1.
*   TODO: Push base configuration to DUT specifying an interface configuration
    for DUT port-1.
*   Push configuration using SetRequest specifying:

    *   `origin: ""` (openconfig, default origin) - containing modelled
        configuration.

    *   `origin: "cli"` - containing:

        ```
        interface <DUT port-1>
        shutdown
        ```

*   Validate that DUT port-1 is shown as shutdown through telemetry.

*   Validate that ATE port-1 reports that DUT port-1 is down.

*   Run CLI command with GetRequest specifying `origin: "cli"`:

    *   `show version` and `show lldp neighbors`
    *   Validate CLI response is generated by DUT.

## Config Parameter coverage

## Telemetry Parameter coverage