---
title: "Blank screen after update video drivers"
date: 2014-08-12
forum: General Help
---

### Post by paradox103 on 2014-08-12
Hi
I recently installed Ubuntu 14.04 LTS. I updated my graphic driver by going to System Settings -> Software & updates -> Additional Drivers. I selected the Video driver for AMD graphics accelerators from fglrx (proprietary). After the driver installed and I rebooted, the login screen was black. My monitor said the signal was out of range. Having experienced this in 12.04 I followed instructions to execute a script when LXDM starts to change the resolution of the login screen. I have altered /etc/lightdm/lightdm.conf and added the line display-setup-script=/usr/share/lightdmxrandr.sh which is executable and it's contents are ```
!/bin/sh
xrandr --output VGA-0 --primary --mode 1024x768

``` I was able to access a terminal (CTRL-ALT-F2) to uninstall the driver ```
sudo apt-get remove --purge fglrx fglrx-amdcccle 
```
I want to use the proprietary driver because the open source driver gives me a maximum of 1024x768 resolution. Any ideas?

---

### Post by paradox103 on 2014-10-01
Problem solved. I ended up buying a new monitor.

---

