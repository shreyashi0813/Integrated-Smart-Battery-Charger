# Integrated Smart Charging System 

**Patent application:** 202541062114  
**Publication date supplied:** 30 June 2025  
**Title:** Integrated Smart Charging System

An integrated smart charging system concept for miniature electronic devices, combining analog overcharge cut-off, ESP32-based monitoring, charging-time estimation, and user feedback.


## Overview

The supplied specification describes a compact charging and energy-management architecture intended for devices such as earbuds, hearing aids, toys, and small consumer electronics. It combines a hardware protection path with microcontroller-driven digital supervision, user feedback, and switching of the output path when the primary battery reaches its full-charge condition.

## Features Described in the Specification

- Voltage and current sensing for charging-state monitoring
- NE555-based analog overcharge protection path
- Transistor-driven relay control to disconnect the primary charging path
- ESP32-based monitoring and control
- EEPROM storage/retrieval of historical charging-session data
- Estimated time-to-full-charge calculation
- 16×2 LCD display for charging parameters and status
- Buzzer alerts for abnormal charging conditions
- Automatic power redirection to a secondary USB-connected device after full-charge detection
- Child-safe mode concept with predefined voltage/current limits
- Manual reset and trigger controls

## High-Level Architecture

```text
Primary Li-ion Battery / Input Power
                |
                v
       Voltage + Current Sensors
                |
        +-------+------------------------+
        |                                |
        v                                v
 Analog Protection Path          ESP32 Supervisory Control
 NE555 threshold stage            Sensor sampling and logic
        |                         EEPROM / charge-time estimate
 Transistor + Relay                         |
        |                                   +----> 16×2 LCD
        |                                   +----> Buzzer
        +------------------+----------------+
                           |
                           v
                    Charging-path control
                           |
                    Full charge detected
                           
            
```


## Main Hardware Elements

| Component | Role described in the specification |
|---|---|
| Li-ion battery | Primary battery being charged |
| Voltage sensor | Monitors battery/charging voltage |
| Current sensor | Monitors charging current |
| NE555 timer | Analog threshold / overcharge protection stage |
| Potentiometer | Sets the analog reference threshold |
| BC547 / BC548 transistor | Drives the relay-control path |
| Relay module |
| ESP32 | Digital monitoring and supervisory control |
| EEPROM | Stores historical charging-session data |
| 16×2 LCD | Displays charging parameters and estimated time |
| Piezo buzzer | Audible fault alert |


## Operating Sequence

1. Read charging voltage and current from the sensor modules.
2. Monitor the charging state through the analog protection path and ESP32 control logic.
3. Use the NE555 threshold stage to trigger relay cut-off if the configured overvoltage threshold is crossed.
4. Store charging-session information and estimate time to full charge using historical data, as described in the specification.
5. Show live charging parameters and status on the LCD.
6. Trigger an audible warning and disconnect the relay output when abnormal conditions are detected.




## Safety and Scope

- This is a project concept and documentation summary, not a certified battery charger or battery-management system.
- Lithium-ion cells require appropriate cell-specific charge control, voltage/current limits, thermal monitoring, and independent protection. A generic NE555/relay design alone must not be assumed to provide complete battery safety.
- Verify the actual circuit, cell chemistry, component ratings, isolation, and charge-control method before connecting a real battery.
- Publish only patent material and design artefacts that are publicly disclosed or approved for release.



## License

No license has been selected yet. Until one is added, reuse rights are not granted by this repository. Add a license only after confirming the rights to license all included code, drawings, and other material.
