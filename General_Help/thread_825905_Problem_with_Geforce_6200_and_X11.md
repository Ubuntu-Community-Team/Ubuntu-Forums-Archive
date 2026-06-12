---
title: "Problem with Geforce 6200 and X11"
date: 2008-06-11
forum: General Help
---

### Post by collinp on 2008-06-11
Ok, when i try to boot after installing the Geforce 6200, it gets past the loadup screen, but where im supposed to login, there is a black screen. Can someone help me?

---

### Post by Mochtroid-X on 2008-07-19
I had this exact same problem with a computer I was building for a friend.

Boot the system up with the live CD, but at the boot menu switch it to boot in "Safe Graphics Mode" with F4. the system should boot normally and get you to the desktop.

Once at the desktop, mount your hard drive open a terminal and enter this:
```
sudo gedit
```

Find the xorg.conf on your hard drive (/media/disk/etc/X11/xorg.conf for me) and change the video driver to **vesa** like this:

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "vesa"
EndSection
```

Save the xorg.conf annd reboot to your hard drive. It should take you to the desktop with no problem. At this point, goto the restricted drivers manager and install the proprietary Nvidia driver. Reboot and everything should work fine.


Optionally, install nvidia-settings with:
```
sudo apt-get install nvidia-settings
```

The shortcut for NVIDIA X Server Settings needs to be run as root for any changes to be permanent, so you'll have to edit it to run as this:
```
gksudo nvidia-settings
```

Then, enter your xorg.conf and modify "Configured Video Device" to use Coolbits:
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    Option         "Coolbits" "1"
EndSection
```

...and enjoy overclocking should you feel so inclined. :)

---

