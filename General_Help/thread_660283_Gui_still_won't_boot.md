---
title: "Gui still won't boot"
date: 2008-01-06
forum: General Help
---

### Post by Dracar on 2008-01-06
My gui still wont boot, it just stopped at some point, i ran the one command line to automatically set it up, the xserver thing, and now it just gives me a blue screen with an error on boot then goes to like cmd on me. any onther ideas?

---

### Post by sq377 on 2008-01-06
When it is booting up, press escape when it says so and select recovery mode.  When that boots you into a terminal, type
```
sudo nano /etc/X11/xorg.conf
```
go down to the device section, mine looks like this:
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7900 GS"
EndSection
```

change the Driver line to say
Driver "vesa"

Without knowing your exact video card it's a little hard to say what driver, but usually vesa is a safe bet.  If that doesn't work, try "ati" if an ati card, or "nv" if nvidia.  Unless it is an older card it isn't likely to have 3d acceleration, but restricted-manager should pop up when the desktop boots and assist you in installing the correct driver.

Good luck

---

