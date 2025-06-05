![IMG_20250529_183928](https://github.com/user-attachments/assets/c752d6a8-b048-4f54-90b1-becba405593c)![IMG_20250529_183928](https://github.com/user-attachments/assets/957601a2-3751-48bd-a215-9d49b7f53721)![IMG_20250529_183928](https://github.com/user-attachments/assets/72089270-5575-4a99-a87f-5df2b02fc0e9)# HuskyLens Face Recognition Relay Lock

This Arduino project uses a [HuskyLens AI Camera](https://www.dfrobot.com/product-1922.html) with face recognition to control a relay lock. It identifies authorized faces and unlocks the relay for them, automatically locking it again when they leave.

## 🧠 Features

- Face recognition using HuskyLens AI camera.
- Relay (electronic lock) control based on authorized face IDs.
- Cooldown period after locking to prevent rapid toggling.
- Serial output for debugging and status updates.

## 🛠️ Hardware Required

- Arduino (Uno, Mega, or compatible)
- [HuskyLens AI Camera](https://www.dfrobot.com/product-1922.html)
- I2C connection (usually A4/A5 on Uno)
- Relay module
- Power supply for relay/lock
- Jumper wires

## ⚙️ Wiring

| Component    | Arduino Pin |
|--------------|--------------|
| HuskyLens SDA | A4           |
| HuskyLens SCL | A5           |
| Relay IN     | D3           |
| VCC/GND      | 5V/GND       |

> Ensure HuskyLens is set to **I2C protocol** via:  
> *General Settings → Protocol Type → I2C*

## 🧑‍💻 How It Works

1. HuskyLens is trained to recognize faces and assign them an ID.
2. The sketch checks if a recognized face is present.
3. If a face with ID 1 or 2 is detected:
    - The relay is unlocked.
4. If the face disappears:
    - The relay is locked.
    - A 5-second cooldown is applied before it can unlock again.

## 📝 Arduino Code Overview

```cpp
#define RELAY_PIN 3
#define COOLDOWN_DURATION 5000



