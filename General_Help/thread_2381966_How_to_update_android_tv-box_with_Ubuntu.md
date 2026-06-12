---
title: "How to update android tv-box with Ubuntu?"
date: 2018-01-07
forum: General Help
---

### Post by x3ua on 2018-01-07
I have D32 TV-box and it's booted to recovery mode. I've chosen "apply update from adb" and it gives message:
"Now send the package you want to apply to the device with "adb sideload <filename>"..."

but "adb devices" found nothing

Even lsusb cant find device

TV-box is connected to PC with USB2USB cable and I've updated box with it using Windows software.

---

### Post by x3ua on 2018-01-07
I managed found it with lsusb. I had to connect it without power supply.

$ lsusb
Bus 001 Device 011: ID 2207:320b 

$ ls -l /dev/bus/usb/001
crw-rw-rw- 1 root root 189, 10 Jan  7 16:15 011

Still adb devices do not find it.

$ cat /etc/udev/rules.d/51-android.rules
# TV-box Nexsmart D32
SUBSYSTEMS=="usb", ATTRS{idVendor}=="2207", ATTRS{idProduct}=="320b", MODE="0666"

---

### Post by x3ua on 2018-01-07
[h=3]Linux Upgrade Tool worked.[/h]http://www.hotmcu.com/wiki/Flashing_Firmware_Image_Files_Using_The_Rockchip_Tool#Using_Linux_Upgrade_Tool_to_flash_update.img

---

