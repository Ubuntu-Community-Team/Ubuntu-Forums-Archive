---
title: "Heron Extra Visual Effects - Nvidia Drivers"
date: 2008-05-09
forum: General Help
---

### Post by cheese1985 on 2008-05-09
Hi,

I have recently tried to get Hardy Heron working on my new PC. Installation has been fine until I try to activate the extra visual effects. When I select extra effects the resolution changes to a 640X480. When I try to make the resolution bigger I can't because the only options the Nvidia X Server Setting allow me to select are 320X240 and 640X480.

If I disable extra visual effects, I am able to select much higher resolutions.

Computer Specs:
- Gigabyte GA M57SLI-S4 SKT AM2 Nvidia MCP55P PCI-E 8Channel audio ATX
- AMD Athlon 64 X2 6400+ (3.2 GHz) Socket AM2 L2 2MB (2x1MB) Retail Boxed Processor
- 2X Crucial 2GB kit (2x1GB) DDR2 533MHz/PC2-4200 Memory Non-ECC Unbuffered CL4 Lifetime Warrant
- Inno3D 8800GT 512MB GDDR3 Wind Edition Cooler Dual DVI TV Out PCI-E Graphics Card

I had a sneak peek at the /etc/X11/xorg.conf file, but being a bit of a noob when it comes to linux, I became lost very quickly.

Here's what the files says anyways:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection
```

I know I might have to change the /etc/X11/xorg.conf file, but I have no idea what to do with it!

I've also downloaded the Nvidia restricted drivers, but the same problem is still there.

Does anyone know where the problem lies and how best to fix it?

Many thanks guys,
Cheese

---

### Post by quasimodo69 on 2008-05-10
> **cheese1985 said:**
> Hi,

I have recently tried to get Hardy Heron working on my new PC. Installation has been fine until I try to activate the extra visual effects. When I select extra effects the resolution changes to a 640X480. When I try to make the resolution bigger I can't because the only options the Nvidia X Server Setting allow me to select are 320X240 and 640X480.

If I disable extra visual effects, I am able to select much higher resolutions.

Computer Specs:
- Gigabyte GA M57SLI-S4 SKT AM2 Nvidia MCP55P PCI-E 8Channel audio ATX
- AMD Athlon 64 X2 6400+ (3.2 GHz) Socket AM2 L2 2MB (2x1MB) Retail Boxed Processor
- 2X Crucial 2GB kit (2x1GB) DDR2 533MHz/PC2-4200 Memory Non-ECC Unbuffered CL4 Lifetime Warrant
- Inno3D 8800GT 512MB GDDR3 Wind Edition Cooler Dual DVI TV Out PCI-E Graphics Card

I had a sneak peek at the /etc/X11/xorg.conf file, but being a bit of a noob when it comes to linux, I became lost very quickly.

Here's what the files says anyways:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection
```

I know I might have to change the /etc/X11/xorg.conf file, but I have no idea what to do with it!

I've also downloaded the Nvidia restricted drivers, but the same problem is still there.

Does anyone know where the problem lies and how best to fix it?

Many thanks guys,
Cheese
first try using Envy to uninstall and reinstall the nvidia drivers.
Then use terminal and type *sudo displayconfig-gtk* and use the display config to choose a minitor-or one pretty close to it.if it asks you for a driver file,just close that dialog box and restart.
  I had the same problem and that is how I fixed it.
You can search out my other posts and see Kirios helped me find the solution in one of the other posts and there is a link to it there.Hope this works for you>

---

### Post by tekniche on 2008-05-15
I tried using envy to install the drivers and it did not work. I am going to try the command you mention though because as of right now my screen is displaying incorrectly ( right res, wrong position) and I can not enable desktop effects. I think it is a problem with the nvidia drivers but your post makes me wonder if the issue is actual with the OS not seeing the monitor properly. I will let you know how it goes.

---

### Post by asmiller-ke6seh on 2008-05-15
Could it be that the Desktop Effects subsystem knows something not obvious to us? How much memory do you have on that GPU board? I am just guessing, here, but maybe it polls the GPU and sees that with the amount of memory there that Desktop Effects can only be supported at a lower resolution? Just a guess, though.

---

### Post by tekniche on 2008-05-16
> **asmiller-ke6seh said:**
> Could it be that the Desktop Effects subsystem knows something not obvious to us? How much memory do you have on that GPU board? I am just guessing, here, but maybe it polls the GPU and sees that with the amount of memory there that Desktop Effects can only be supported at a lower resolution? Just a guess, though.

I am not entirely sure. That is quite possible though. My situation is that I can not get the desktop effects at any resolution. It is either the right resolution without the desktop effects or its in "low graphics mode." I have tried many different things trying to get this to work and after dpkg-reconfigure gdm and dpkg-reconfigure xserver-xorg and reinstalling the driver I am getting the splash screen for the beta drivers and everything appears to be working properly except I have no desktop effects and the screen is pushed over to the right about a quarter of an inch. I was not able to autoconfig the monitor or anything so I believe that there is still a compatibility issue with the herron kernel and the nvidia beta drivers. I'm stumped! Any help would be greatly appreciated.

---

