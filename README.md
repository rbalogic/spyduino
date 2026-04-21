# Spyduino 🕵️‍♂️🤖

Spyduino is a simple yet effective DIY security system that uses an Arduino-connected ultrasonic sensor to detect intruders nearing your computer. When someone enters the specified range, it automatically triggers your webcam to capture their image.

![Arduino Sketch Schema](ultrasonic_sensor_bb.png)

## 🚀 Features
- **Real-time Detection:** Uses HC-SR04 ultrasonic sensor for proximity sensing.
- **Auto-Capture:** Automatically snaps a photo using the system's webcam via Python.
- **Customizable Range:** Easily adjust the sensitivity/distance threshold.
- **Silent Operation:** Runs in the background, monitoring serial data from the Arduino.

## 🛠 Hardware Requirements
- **Arduino Board** (Uno, Nano, Mega, etc.)
- **Ultrasonic Sensor** (HC-SR04)
- **USB Cable** (to connect Arduino to PC)
- **Webcam** (built-in or USB)
- **Jumper Wires & Breadboard**

### Wiring Diagram
| Ultrasonic Sensor | Arduino Pin |
|-------------------|-------------|
| VCC               | 5V          |
| Trig              | Pin 13      |
| Echo              | Pin 11      |
| GND               | GND         |

## 💻 Software Requirements
- **Arduino IDE**
- **Python 2.7+** (The current script uses Python 2 syntax)
- **Python Libraries:** `pyserial`, `pygame`

## 📥 Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/spyduino.git
   cd spyduino
   ```

2. **Install Python dependencies:**
   ```bash
   sudo pip install -r requirements.txt
   ```

3. **Setup Arduino:**
   - Open `arduino/ultra_sonic_sensor/ultra_sonic_sensor.ino` in the Arduino IDE.
   - Connect your Arduino and select the correct port.
   - Click **Upload**.

## 🏃 Usage

1. **Identify the Serial Port:**
   Find the port your Arduino is connected to (e.g., `/dev/ttyUSB0` on Linux/macOS or `COM3` on Windows).

2. **Run the Capture Script:**
   ```bash
   python python/capture_user.py [YOUR_SERIAL_PORT]
   ```
   Example: `python python/capture_user.py /dev/ttyUSB0`

3. **Check Captured Images:**
   Photos are saved in the `$HOME/image_captured/` directory. 
   *Note: Ensure this directory exists or create it with `mkdir ~/image_captured`.*

## ⚙️ Customization

You can adjust the sensitivity by modifying the `RANGE` variable in `python/capture_user.py`:

```python
# Adjust this value to change detection distance
RANGE = 300 
```

The sensor sends raw pulse duration to the script. A lower `RANGE` value means the intruder must be closer to trigger the camera.

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
