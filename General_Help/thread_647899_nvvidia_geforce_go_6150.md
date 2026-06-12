---
title: "nvvidia geforce go 6150"
date: 2007-12-22
forum: General Help
---

### Post by roquemartins on 2007-12-22
I have installed Ubuntu 7.10 and everything is OK except the Screen 
Resolutions Preferences . The  default settings available are 800x600
and 640x480 and I need 1280x800.
Thanks in advance for any help

Roque

---

### Post by taurus on 2007-12-22
Have you install nvidia driver for your graphic card?  You can do that from System -> Administration -> Restricted Drivers Manager.

Once you've installed nvidia, you need to reboot and then you can change it to whatever resolution you want to use.

---

### Post by jken146 on 2007-12-22
First, try enabling the restricted driver.  Then reboot.  Look in Screen Resolution in the menus and run **nvidia-settings** to see if you can get the desired res.

If that doesn't do it, press Ctrl+Alt+F1 and run the following commands. ```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start
```

---

