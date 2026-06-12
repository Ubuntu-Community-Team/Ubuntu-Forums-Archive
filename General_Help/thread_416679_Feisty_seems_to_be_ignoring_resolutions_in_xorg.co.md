---
title: "Feisty seems to be ignoring resolutions in xorg.conf"
date: 2007-04-21
forum: General Help
---

### Post by speedsix on 2007-04-21
My xorg.conf is setup as follows, edgy used to just show the 2 resolutions I have specified but feisty seems to show everything retrieved from the eid, in System>Preferences>Screen Resolution

Also, it lists the refresh rate as 50Hz when I select 1280x1024 but my monitor is reporting it is receiving 60Hz.

```

Section "Screen"
        Identifier      "DellScreen"
        Device          "dev1"
        Monitor         "DellMonitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024_60" "640x480_60"
        EndSubSection
EndSection

```

---

### Post by Dave54 on 2007-04-21
I have the same problem of mis-matched refresh rates. I'm following a few other threads:
[http://ubuntuforums.org/showthread.php?t=417716]("http://ubuntuforums.org/showthread.php?t=417716")
[http://ubuntuforums.org/showthread.php?t=415893]("http://ubuntuforums.org/showthread.php?t=415893")
[http://ubuntuforums.org/showthread.php?t=414287]("http://ubuntuforums.org/showthread.php?t=414287")
I'll post if I find a solution.

Edit: have you tried adding
```
    Option         "UseEdidFreqs" "false"
```
to the Screen section of your xorg?

---

### Post by speedsix on 2007-04-23
It's not a massive problem as I can get the resolution/refresh rates I want, just a bit odd the resolution chooser seems a bit screwy. It shows resolutions that I haven't listed in my xorg.conf (some the monitor doesn't even support) and also the refresh rates aren't correct.

---

### Post by rumli on 2007-04-23
I partially fixed my resolution problems by using 
```
Option "UseEdid" "false"
```

I say "partially fixed" because I use dual monitors, and it works for one of the monitors but not the other.

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

### Post by speedsix on 2007-04-25
That fixes the problem of wacky refresh rates showing up but still shows all the resolutions retrieved from the eid rather than only the two I've specified in xorg.conf. (1280 & 640)

This is only for my first monitor though, my second x display only shows the 3 res I specified in xorg.conf. Odd. Not really a problem, just different from how edgy worked.

---

