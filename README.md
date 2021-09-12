# cpu_trottle
Trottles CPU when getting hot - Python3 cli tool which can be run as a daemon systemd service.

CPU Trottle is released under the terms of the GNU GPLv3 License.

Must be tested of different kind of hardware and linux kernel verions. Works on modern AMD and Intel with Linux Kernel 5.4 and newer.

Required packages
-----------------
This script requires package: cpufrequtils
Install command for Ubuntu based distro's: sudo apt install cpufrequtils

How to stress test the CPU
--------------------------
Stress testing cpu with command: stress -c 4 -t 120s
With c the number of threads and t time in seconds to stress test.

Install helpful Gnome extensions
--------------------------------
You can install Gnome extensions on https://extensions.gnome.org/
Very helpful tools are: cpufreq and Freon for temperature and cpu speed measurements

Make this script run as a systemd service
----------------------------------------
Instructions for running the script as a systemd service daemon:
Step 1.
sudo nano /etc/systemd/system/cpu_trottle.service

[Unit]
Description=Trottles cpu speed at defined temperature
After=multi-user.target

[Service]
Type=simple
Restart=always
ExecStart=/usr/bin/python3 /home/<username>/cpu_trottle.py

[Install]
WantedBy=multi-user.target

Step 2.
sudo systemctl daemon-reload

Step 3.
sudo systemctl enable cpu_trottle.service
sudo systemctl start cpu_trottle.service
