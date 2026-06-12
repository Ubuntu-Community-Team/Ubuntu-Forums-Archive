---
title: "New installation, freezing after several minutes, syslog engind with zeroes"
date: 2020-01-27
forum: General Help
---

### Post by ruwolf on 2020-01-27
Hello.

I have installed Xubuntu on new computer.
It freezes after several minutes after reboot, cca 20 to 120.
After freezing, nothing from keyboard can be done: Unable to switch to virtual consoles, even [Alt]+[SysReq/PrnScr]+([R]+[E]+[I]+[S]+[U]+[B]) is not working.
Syslog contains hundreds (cca 200 800 pieces of null bytes) zeroes (not 0, ASCII code 0x30, but \0, ASCII code 0x00) on the end, i.e. before next reboot.

Please, how can I debug or inspect cause of this unwanted behavior?

System information:
MB: ASUS Prime X570-Pro
CPU: AMD Ryzen 5 3600
RAM: 32 GiB
swap: none
SSD: HP EX920 M.2 1TB
Graphics: GigaByte NVidia GeForce GTX 1650 Super OC 4G rev. 1.0
Xubuntu: 19.10 eoan
kernel: 5.3.0-26-generic
xorg-server: 2:1.20.5+git20191008-0ubuntu1

---

### Post by CelticWarrior on 2020-01-27
You need to install the Nvidia proprietary drivers.

---

### Post by oldfred on 2020-01-27
There was a major update to UEFI last summer from AMD, but vendors did not roll out until last fall in UEFI updates.
Have you updated UEFI? and SSD firmware?

AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates in Aug as a "beta" though without explicitly acknowledging the Linux fix.

---

