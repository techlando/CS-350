# # CS-350
# # Emerging Sys Arch &amp; Tech

# # Summarize the project and what problem it was solving.
# Thermostat Prototype (Thermostat.py)

A Python implementation running on a Raspberry Pi that reads room temperature via an I²C sensor, drives heating and cooling LEDs with PWM, manages a three‑state machine (Off, Heat, Cool), updates a 16×2 LCD, and sends serial updates every 30 seconds. This artifact is based on the Thermostat_lab.docx specification and demonstrates low‑level hardware control and state‑machine design.

The Thermostat Prototype automated temperature regulation logic on a Pi board. It solved the need for a simple, reliable IoT thermostat: reading sensor data, updating display and LEDs, cycling modes with a button, and reporting status over UART for remote monitoring

# Temperature Sensor Integration (TemperatureSensorIntegration.py)

A Python–state‑machine example that displays temperature and humidity on a 16×2 LCD, toggling between Celsius and Fahrenheit when a button is pressed. It shows clean separation of display management, sensor reading and button‑driven state transitions.

Temperature Sensor Integration addressed the challenge of toggling display units in embedded UI. It provided a clear, real‑time way to switch between Celsius and Fahrenheit on a basic character LCD, enforcing good state‑machine practices and thread‑safe UI updates.

# What did you do particularly well?

Modular State‑Machine Design: In both projects, I encapsulated modes and transitions in classes (TemperatureMachine, TempMachine), making each state’s entry and exit actions explicit.

Hardware Abstraction: I wrote reusable wrappers for GPIO, PWM, I²C sensor reads and serial I/O, so switching hardware platforms or adding features requires minimal code changes.

Robust Serial Protocol: In the thermostat code, I built comma‑delimited reporting with checksum logic and timeout handling, ensuring the server‑simulator script (ThermostatServer‑Simulator.py) receives only complete, validated packets.

# Where could you improve?

Automated Testing: I relied on manual hardware tests. Next time, I’ll add host‑based emulation or mock libraries for the sensor and GPIO interfaces to run unit tests without a Pi.

Documentation Depth: My code comments explain “what” functions do, but I could add design rationale for choice of threading model and timing intervals.

Resource Optimization: On the Pi there’s ample memory, but I can apply ring buffers or circular queues in my UART parser to prepare for tighter microcontroller environments.


# What tools and/or resources are you adding to your support network?

Adafruit Sensor and LCD Libraries documentation for I²C peripherals

gpiozero and statemachine Python packages to streamline GPIO and state‑machine code

Stack Overflow threads on Python threading with GPIO and serial I/O

Course lab documents (Thermostat_lab.docx) as authoritative design references


# What skills from this project will be particularly transferable to other projects and/or course work?

Embedded State‑Machine Implementation in Python/C, applicable to RTOS tasks in C/C++

Peripheral Integration: sensor reading, PWM control and serial communication

Threading and Concurrency: updating displays in background threads while main logic runs

Protocol Design: simple ASCII packet formats with validation and acknowledgement

Modular Code Organization: separating drivers, logic and UI for easier scaling and maintenance



# How did you make this project maintainable, readable, and adaptable?

Flat Repository Structure with Clear Names: All project artifacts (Thermostat.py, ThermostatServer-Simulator.py, TemperatureSensorIntegration.py, and Thermostat_lab.docx) reside at the top level with descriptive filenames, making them easy to locate and understand.

Inline Hardware Parameters: Pin assignments, PWM channels, serial port settings and timing intervals are defined directly in each script’s setup section, making it straightforward to adjust hardware configurations.

Meaningful Names: Functions like updateLights(), setupSerialOutput() and manageMyDisplay() immediately convey intent


