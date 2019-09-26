# iFit Pedaler
This project just basically sends a low and high signal at a regular interval to simulate an aerobic equipment pedaling.

## Connection
You will need to connect two wires from your Raspberry Pi to your aerobic console pinout:
1. The "data" pin, which should be one of the valid BCM data pins (see https://pinout.xyz/)
2. Ground pin

I'll admit I know nothing about the pinouts on the aerobic consoles. In my case, on a Pro-Form elliptical console, the data pin is connected to the far left pin, and the ground pin is connected to the pin right next to it. ¯\_(ツ)_/¯

## Cloning & Installation
This script should get most things up and running from a fresh Raspbian install, assuming it has network configured.
```
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install git python-pip
pip install gpiozero

cd ~/
git clone https://github.com/williamt-ifit/ifitpedaler.git
sudo mv ifitpedaler/pedal /usr/local/bin/pedal
rm -rf ifitpedaler
```
Running that script should install the necessary dependencies, clone the repo, and move the executable to `/usr/local/bin` for easy use. 

## Usage
```
usage: pedal [-h] [-p PIN] [--on ONTIME] [--off OFFTIME] [-r RPM] [-v]

Enables and disables a provided BCM pin at the provided rates.

optional arguments:
  -h, --help         show this help message and exit
  -p PIN, --pin PIN  The BCM pin number to toggle.
  --on ONTIME        The duration, in milliseconds, for the pin to be enabled.
  --off OFFTIME      The duration, in milliseconds, for the pin to be
                     disabled. By default, this value is the same as the
                     ONTIME value.
  -r RPM, --rpm RPM  Approximate RPM to pedal at.
  -v, --verbose
```
