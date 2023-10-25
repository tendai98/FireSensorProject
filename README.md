# Fire Sensing Project using ESP8266

The Fire Sensing Project is a system that employs an ESP8266 microcontroller to monitor temperature and the presence of fire through an infrared (IR) sensor. It includes an alarm feature and serves the data to a mobile app for control and monitoring. This README provides an overview of the project structure and its functionality, using the provided code as source material.

## Project Structure

The project consists of several code files:

- `alarm.h`: Defines functions for initializing and triggering an alarm.
- `wifi.h`: Configures WiFi settings for the ESP8266.
- `server.h`: Sets up an HTTP server to handle requests and serve data.
- `temperature.h`: Manages the temperature sensor (DS18B20) and retrieves temperature values.
- `ir.h`: Deals with the IR sensor (infrared) and detects the presence of fire.
- `FireSensorProject.ino`: The main project file that combines these components and controls the overall behavior of the system.

## Code Overview

### Alarm (`alarm.h`)

The `alarm.h` file provides functions for working with a buzzer or alarm:

- `initAlarm()`: Initializes the alarm (buzzer) by setting the GPIO pin as an output.
- `triggerAlarm()`: Triggers the alarm by setting the GPIO pin to a high (ON) state.

### WiFi Configuration (`wifi.h`)

The `wifi.h` file handles WiFi configuration for the ESP8266:

- `initNET()`: Configures the ESP8266 to act as an access point with a specific SSID and password.
- `blinkLED()`: Provides a function to visually indicate network activity by blinking an LED.

### Server Setup (`server.h`)

The `server.h` file defines the HTTP server and handles data serving and request handling:

- `getData()`: Retrieves and serves temperature, IR sensor state, and location information.
- `resetSensor()`: Allows resetting the sensor or device.
- `deadEnd()`: Handles any undefined or invalid routes.
- `initServer()`: Sets up the HTTP server, defines endpoints, and starts the server.

### Temperature Sensor (`temperature.h`)

The `temperature.h` file manages the temperature sensor (DS18B20) and temperature retrieval:

- `setupTemperatureSensor()`: Initializes the temperature sensor.
- `getTempValue()`: Retrieves the temperature value in Celsius from the sensor.

### IR Sensor (`ir.h`)

The `ir.h` file deals with the IR sensor to detect the presence of fire:

- `setupIRSensor()`: Initializes the IR sensor by setting the GPIO pin as an input.
- `getIRSensorState()`: Retrieves the state of the IR sensor (high/low) to detect fire presence.

### Main Code (`FireSensorProject.ino`)

The `FireSensorProject.ino` file combines the functionality of all the components and controls the overall behavior of the system. It sets up the temperature sensor, IR sensor, WiFi, server, and alarm. It continuously serves data, including temperature, IR sensor state, and location information.

## Usage

1. Ensure you have the necessary libraries installed in your Arduino IDE. This project may use libraries specific to the DS18B20 temperature sensor and the OneWire communication protocol.

2. Modify WiFi configuration in the `wifi.h` file to match your network settings, including SSID and password.

3. Upload the project code (`FireSensorProject.ino`) to your ESP8266 controller.

4. The ESP8266 will create a WiFi access point with the SSID "Fire-Monitoring-System" and password "1234567890."

5. Connect your mobile app to the WiFi access point created by the ESP8266.

6. Open your mobile app to receive data from the ESP8266, including temperature, IR sensor state, and location information.

7. Monitor and control the system from your mobile app. The alarm will be triggered if the temperature exceeds a specified threshold or if the IR sensor detects fire.

8. To reset the sensor or device, access the "/reset" endpoint through a web browser or mobile app.

## Note

- This code is designed for educational purposes and may require modifications to work with your specific hardware and network setup.

- Make sure that your sensors are correctly wired to the ESP8266 and powered as needed.

- The provided code and structure can be expanded upon to add more features or integrated into a complete fire monitoring and alarm system.
