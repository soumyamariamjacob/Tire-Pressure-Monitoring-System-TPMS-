# Tire-Pressure-Monitoring-System-TPMS
1. Overview

The Tire Pressure Monitoring System (TPMS) is designed to continuously monitor the air pressure inside pneumatic tires on vehicles and alert the driver when the pressure falls below a predetermined threshold. Maintaining proper tire pressure is crucial for vehicle safety, fuel efficiency, and tire longevity. This project utilizes pressure sensors connected to a microcontroller to measure and transmit real-time tire pressure data to a display unit, providing visual and audio alerts in case of low pressure.

2. Components Required

Microcontrollers:

ESP32 Development Board (2 units): One for sensing and transmitting data, another for receiving and displaying data.

Pressure Sensors:

MPX5700AP Analog Pressure Sensors (4 units): To measure the pressure of each tire.

Display Unit:

1.3-inch I2C OLED Display: To display real-time tire pressure readings and alerts.

Audio Alert:

Buzzer: For audio alerts when tire pressure is low.

Power Supply:

3.7V Li-Po Batteries: To power the ESP32 boards and sensors.

Miscellaneous:

Voltage Regulators (e.g., AMS1117 3.3V): To provide stable voltage to sensors and microcontrollers.

Breadboards and Jumper Wires

Enclosures: To protect the electronics.

Pressure Source: For simulating tire pressure during testing (e.g., air pump).

3. System Architecture

The system consists of two main units:

Sensor Unit: Placed near the tires, it reads the pressure data from the sensors and transmits it wirelessly using ESP32's built-in Wi-Fi capabilities.

Display Unit: Located on the vehicle's dashboard, it receives the data wirelessly and displays the pressure readings on an OLED display. It also triggers visual and audio alerts if the pressure drops below safe levels.

4. Circuit Diagrams

4.1 Sensor Unit Connections:

For each tire, the setup is similar. Below is the connection for one pressure sensor. Repeat the same for all four sensors.

Pressure Sensor (MPX5700AP) Connections:

VCC: Connect to 5V output of the voltage regulator.

GND: Connect to common ground.

Output: Connect to one of the ESP32's analog input pins (e.g., GPIO 36).

ESP32 Connections:

VIN: Connect to 5V from the battery.

GND: Connect to common ground.

4.2 Display Unit Connections:

OLED Display Connections:

VCC: Connect to 3.3V on ESP32.

GND: Connect to GND on ESP32.

SDA: Connect to GPIO 21 on ESP32.

SCL: Connect to GPIO 22 on ESP32.

Buzzer Connections:

Positive (+): Connect to GPIO 19 on ESP32 through a current-limiting resistor.

Negative (-): Connect to GND on ESP32.

ESP32 Connections:

VIN: Connect to 5V from the battery.

GND: Connect to common ground.

5. Source Code

5.1 Sensor Unit Code

This code reads pressure data from the sensors and sends it to the display unit over Wi-Fi using ESP-NOW protocol.// Sensor Unit Code
5.2 Display Unit Code

This code receives the pressure data via ESP-NOW and displays it on the OLED screen. It also triggers a buzzer and visual alerts if the pressure drops below a safe threshold.
Tire Pressure Monitoring System (TPMS)

1. Overview

The Tire Pressure Monitoring System (TPMS) is designed to continuously monitor the air pressure inside pneumatic tires on vehicles and alert the driver when the pressure falls below a predetermined threshold. Maintaining proper tire pressure is crucial for vehicle safety, fuel efficiency, and tire longevity. This project utilizes pressure sensors connected to a microcontroller to measure and transmit real-time tire pressure data to a display unit, providing visual and audio alerts in case of low pressure.

2. Components Required

Microcontrollers:

ESP32 Development Board (2 units): One for sensing and transmitting data, another for receiving and displaying data.

Pressure Sensors:

MPX5700AP Analog Pressure Sensors (4 units): To measure the pressure of each tire.

Display Unit:

1.3-inch I2C OLED Display: To display real-time tire pressure readings and alerts.

Audio Alert:

Buzzer: For audio alerts when tire pressure is low.

Power Supply:

3.7V Li-Po Batteries: To power the ESP32 boards and sensors.

Miscellaneous:

Voltage Regulators (e.g., AMS1117 3.3V): To provide stable voltage to sensors and microcontrollers.

Breadboards and Jumper Wires

Enclosures: To protect the electronics.

Pressure Source: For simulating tire pressure during testing (e.g., air pump).

3. System Architecture

The system consists of two main units:

Sensor Unit: Placed near the tires, it reads the pressure data from the sensors and transmits it wirelessly using ESP32's built-in Wi-Fi capabilities.

Display Unit: Located on the vehicle's dashboard, it receives the data wirelessly and displays the pressure readings on an OLED display. It also triggers visual and audio alerts if the pressure drops below safe levels.

4. Circuit Diagrams

4.1 Sensor Unit Connections:

For each tire, the setup is similar. Below is the connection for one pressure sensor. Repeat the same for all four sensors.

Pressure Sensor (MPX5700AP) Connections:

VCC: Connect to 5V output of the voltage regulator.

GND: Connect to common ground.

Output: Connect to one of the ESP32's analog input pins (e.g., GPIO 36).

ESP32 Connections:

VIN: Connect to 5V from the battery.

GND: Connect to common ground.

4.2 Display Unit Connections:

OLED Display Connections:

VCC: Connect to 3.3V on ESP32.

GND: Connect to GND on ESP32.

SDA: Connect to GPIO 21 on ESP32.

SCL: Connect to GPIO 22 on ESP32.

Buzzer Connections:

Positive (+): Connect to GPIO 19 on ESP32 through a current-limiting resistor.

Negative (-): Connect to GND on ESP32.

ESP32 Connections:

VIN: Connect to 5V from the battery.

GND: Connect to common ground.

5. Source Code

5.1 Sensor Unit Code

This code reads pressure data from the sensors and sends it to the display unit over Wi-Fi using ESP-NOW protocol.
5.3 Notes on Code Implementation

ESP-NOW Protocol: ESP-NOW is a connectionless Wi-Fi communication protocol developed by Espressif. It enables multiple devices to communicate with each other without the need for a Wi-Fi network. This makes it suitable for real-time data transmission with low latency.

Pressure Sensor Calibration: The analog readings from the pressure sensors are converted to pressure values in kilopascals (kPa). Calibration is necessary to map the sensor output voltage accurately to pressure values.

Alerts: The display unit checks if any tire pressure falls below the safe threshold and activates the buzzer accordingly. Visual alerts are also provided on the OLED display.

6. Testing and Calibration

6.1 Calibration of Pressure Sensors

Setup Known Pressure Levels: Use a calibrated pressure source to apply known pressure levels to each sensor.

Record Analog Readings: For each known pressure, record the corresponding analog reading from the sensor.

Create Calibration Curve: Plot the pressure values against the analog readings to create a calibration curve.

Implement Calibration in Code: Use the calibration curve to convert analog readings to accurate pressure values in the code.

6.2 Testing the System

Initial Testing: Test each component individually to ensure they work as expected.

Integration Testing: Assemble the entire system and test the communication between sensor and display units.

Simulate Pressure Drop: Gradually reduce the pressure applied to the sensors to test if the system correctly identifies low-pressure conditions and triggers alerts.

Range Testing: Test the wireless communication range between the sensor and display units to ensure reliability within the vehicle.

7. Challenges and Solutions

7.1 Ensuring Accurate Pressure Readings

Challenge: Pressure sensors may produce inaccurate readings due to temperature variations, sensor drift, or electrical noise.

Solution:

Temperature Compensation: Use temperature sensors alongside pressure sensors to compensate for temperature-induced errors.

Sensor Calibration: Regularly calibrate sensors and implement calibration curves in the code.

Signal Filtering: Apply digital filters (e.g., moving average filter) to smooth out noise in sensor readings.

7.2 Reliable Wireless Communication

Challenge: Interference and obstacles within the vehicle can disrupt wireless communication between sensor and display units.

Solution:

Signal Strength Optimization: Adjust the transmission power and use antennas to improve signal strength.

Data Acknowledgment: Implement acknowledgment packets to confirm the successful receipt of data.

Error Checking: Use checksums or CRC methods to detect and correct errors in data transmission.

Alternative Communication Protocols: If ESP-NOW faces interference issues, consider using Bluetooth Low Energy (BLE) or setting up a dedicated Wi-Fi network for communication.

8. Project Enhancements

8.1 Mobile Application Integration Develop a mobile application that can receive tire pressure data via Bluetooth or Wi-Fi, providing an intuitive interface for monitoring and logging data over time.

8.2 Battery Monitoring Include a battery level monitoring system for the sensor units to alert when battery replacement or charging is needed.

8.3 Temperature Monitoring Incorporate temperature sensors to monitor tire temperature alongside pressure, providing more comprehensive data for safety and performance analysis.

8.4 Power Efficiency Implement sleep modes and optimize code to reduce power consumption, extending the battery life of sensor units.

8.5 Alert Customization Allow users to set custom pressure thresholds and notification preferences through the display unit or mobile application.

9. Safety Considerations

Waterproofing: Ensure all electronic components, especially those near the tires, are adequately sealed and waterproofed to prevent damage from moisture and debris.

Robust Enclosures: Use durable enclosures to protect sensors and microcontrollers from physical shocks and vibrations.

Regulatory Compliance: If intended for real-world vehicle integration, ensure the system complies with automotive safety standards and regulations.

10. Conclusion

This TPMS project provides a practical solution for monitoring tire pressure in real-time, enhancing vehicle safety and efficiency. By utilizing readily available components and effective wireless communication protocols, the system offers reliable performance with the potential for further enhancements and integration into more complex vehicle monitoring systems. Proper testing, calibration, and attention to challenges such as accuracy and communication reliability are essential for the successful implementation of this project.
