---
title: "LUBUNTU How to disable nouveau kernel driver to install proprietary drivers ?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
My system is offline and wait to install latest nvidia proprietary driver, but see that need to disable nouveau driver.
I have disabled nouveau driver, but when starting nvidia driver display message that need to disable nouveau kernel driver.
Nouveau driver and nouveau kernel driver are the same component ?
I had done some commands to disable nouveau driver and had breaked the system startup
the commands that I had used are

$ sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo update-initramfs -u
$ sudo reboot

Linux had to be more simple to install drivers in offline mode and also in the list to install drivers in additional drivers show an old version than the latest.
How disable nouveau driver without break system startup ?

---

### Post by CelticWarrior on 2020-08-05
No, I believe you have been told the exact opposite already.
Just install properly the Nvidia driver and that will be used instead of nouveau, no blacklisting required.

Please use Additional Drivers or install by command line the drivers from the official repository, NOT the script from Nvidia. Please do use any internet connection, it's just a few megas therefore negligible. even in a metered connection. Do NOT try alternative ways, especially not using using downloads from Nvidia. Additional Drivers (part of Software & Updates) or a command will install drivers in a matter of seconds.

---

### Post by deadflowr on 2020-08-05
Duplicate thread
closed

(Other thread here
[https://ubuntuforums.org/showthread.php?t=2448254]("https://ubuntuforums.org/showthread.php?t=2448254"))

---

