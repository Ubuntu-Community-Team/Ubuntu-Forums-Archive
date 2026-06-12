---
title: "Feisty - Screen Resolution bug?"
date: 2007-04-19
forum: General Help
---

### Post by plb on 2007-04-19
System Preferences > Screen Resolution says my monitor is at 50Hz while my monitor says it's at 60Hz, anyone else get this?

---

### Post by z987k on 2007-04-19
> **plb said:**
> System Preferences > Screen Resolution says my monitor is at 50Hz while my monitor says it's at 60Hz, anyone else get this?
yep I got that and it doesn't have the correct screen resolution

---

### Post by Dave54 on 2007-04-21
I have the same problem of mis-matched refresh rates. I'm following a few other threads:
[http://ubuntuforums.org/showthread.php?t=417716]("http://ubuntuforums.org/showthread.php?t=417716")
[http://ubuntuforums.org/showthread.php?t=415893]("http://ubuntuforums.org/showthread.php?t=415893")
[http://ubuntuforums.org/showthread.php?t=416679]("http://ubuntuforums.org/showthread.php?t=416679")
I'll post if I find a solution.

---

### Post by Dave54 on 2007-04-24
The solution has been found!

I think the solution only works for nvidia cards, but the problem only occurs if you have an nvidia card ;-) 

Backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Edit your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to "Section "Device"". Within that section, it should have "Driver "nvidia"". Add the following to that section:
```
    Option "DynamicTwinView" "false"
```

So mine looks like this:
```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option         "DynamicTwinView" "false"
EndSection
```

Save and reboot. (or log out and hit ctrl+alt+backspace)

Post if it works :) 

Where this solution came from:
[http://ubuntuforums.org/showthread.php?t=417716]("http://ubuntuforums.org/showthread.php?t=417716")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292")

---

