ESP32 Live Sensor Web Dashboard 🌐

A simple ESP32-based IoT web dashboard for monitoring temperature and humidity using a DHT11/DHT22 sensor and controlling a digital output such as an LED through a web browser.

The ESP32 works as a local web server, so no cloud service or separate server is required. A phone or computer connected to the same Wi-Fi network can access the dashboard.

✨ Features

- 🌡️ Real-time temperature monitoring
- 💧 Real-time humidity monitoring
- 💡 Web-based LED ON/OFF control
- 📱 Responsive dashboard for mobile and desktop
- 📡 Local Wi-Fi communication
- 🔄 Automatic sensor refresh every 2 seconds
- 🔌 JSON API for sensor data and output control
- 💻 HTML, CSS, and JavaScript embedded directly in the ESP32 firmware
- ☁️ No cloud account or external server required

🛠️ Hardware Requirements

- ESP32 development board
- DHT22 or DHT11 sensor
- LED
- 220 Ω resistor
- Breadboard
- Jumper wires
- USB cable

Pin Connections

Component| ESP32 Pin
DHT VCC| 3.3V
DHT DATA| GPIO 4
DHT GND| GND
LED| GPIO 2 through 220 Ω resistor

The example project uses a DHT22 sensor. To use a DHT11, change the sensor type in the Arduino sketch.

💻 Software Requirements

- Arduino IDE or Arduino CLI
- ESP32 Arduino board package
- Adafruit DHT Sensor Library
- Adafruit Unified Sensor Library

Install the required libraries through Arduino IDE's Library Manager, or use Arduino CLI:

arduino-cli core update-index
arduino-cli core install esp32:esp32
arduino-cli lib install "DHT sensor library"
arduino-cli lib install "Adafruit Unified Sensor"

⚙️ Configuration

Open:

ESP32_Sensor_Dashboard.ino

Enter your Wi-Fi credentials:

const char* WIFI_SSID = "YOUR_WIFI_SSID";
const char* WIFI_PASSWORD = "YOUR_WIFI_PASSWORD";

Do not upload real Wi-Fi credentials to a public GitHub repository.

🚀 Upload and Run

1. Connect the ESP32 to your computer.
2. Assemble the DHT sensor and LED circuit.
3. Enter your Wi-Fi SSID and password.
4. Select the correct ESP32 board in Arduino IDE.
5. Select the correct COM/USB port.
6. Compile and upload the sketch.
7. Open Serial Monitor at 115200 baud.
8. Wait for the ESP32 to display its local IP address.
9. Connect your phone or laptop to the same Wi-Fi network.
10. Open the displayed IP address in a web browser.

The dashboard will display temperature, humidity, connection status, and the LED control button.

🔗 API Endpoints

The ESP32 provides three main HTTP endpoints:

Method| Endpoint| Description
GET| "/"| Loads the web dashboard
GET| "/api/data"| Returns temperature, humidity, and output state
POST| "/api/toggle"| Toggles the digital output

Example response from "/api/data":

{
  "temperature": 27.4,
  "humidity": 61.8,
  "output": true
}

📊 Dashboard

The web interface displays:

- Temperature in °C
- Humidity in %RH
- Digital output status
- ON/OFF control button
- Connection status
- Automatic updates every 2 seconds

The dashboard uses JavaScript Fetch API requests to communicate with the ESP32.

🧪 Testing

Expected results:

Test| Expected Result
ESP32 connects to Wi-Fi| Local IP appears in Serial Monitor
Open IP in browser| Dashboard loads
Wait for sensor update| Temperature and humidity update
Press Turn ON| LED turns ON
Press Turn OFF| LED turns OFF
Sensor temporarily fails| Last valid reading is retained

🐛 Troubleshooting

DHT.h not found

Install:

- Adafruit DHT Sensor Library
- Adafruit Unified Sensor Library

Dashboard doesn't open

- Check the IP address shown in Serial Monitor.
- Make sure the ESP32 and phone/computer are connected to the same Wi-Fi network.

Temperature or humidity shows "--"

- Check sensor power.
- Check DATA wiring.
- Confirm the correct DHT sensor type.
- Check the configured GPIO pin.

LED doesn't work

- Check LED polarity.
- Check the 220 Ω resistor.
- Check the GND connection.
- Verify GPIO 2 wiring.

🔮 Future Improvements

Possible future enhancements include:

- 📈 Temperature and humidity history charts
- 🔔 Temperature alerts
- 📶 Wi-Fi RSSI and uptime information
- 💡 Multiple output controls
- ➕ Support for additional sensors
- 📁 LittleFS-based web files
- 🔐 Authentication for trusted networks

⚠️ Safety

This project is intended as a low-voltage electronics prototype.

Do not connect household/mains voltage directly to the breadboard circuit. If a relay is added in the future, use an appropriate low-voltage relay module and follow its documentation.

📁 Project Structure

ESP32-Live-Sensor-Dashboard/
│
├── ESP32_Sensor_Dashboard.ino
├── README.md
└── screenshots/
    ├── dashboard.png
    ├── serial-monitor.png
    └── hardware.jpg

📚 References

- Espressif Arduino-ESP32 documentation
- Arduino software
- Adafruit DHT Sensor Library
- Adafruit Unified Sensor Library

👨‍💻 Project

ESP32 Live Sensor Web Dashboard

Built using ESP32 + Arduino + DHT11/DHT22 + HTML/CSS/JavaScript.
