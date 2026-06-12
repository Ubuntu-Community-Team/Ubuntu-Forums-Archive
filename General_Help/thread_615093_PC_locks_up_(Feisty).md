---
title: "PC locks up (Feisty)"
date: 2007-11-16
forum: General Help
---

### Post by mustbealennox on 2007-11-16
My PC locks up at least once a day, and I have to reboot it. The screen freezes (but does not go blank), and the mouse and keyboard are unresponsive. This occurs while using the computer (i.e. not when it hibernates).

I have a dual-boot installation, with Feisty installed on its own disk. It is running the 2.6.20-16-generic kernel.

The following applications are usually running when it happens:
- Gaim
- Firefox
- Thunderbird
- VNC viewer
- VPN client (for work)

Is this type of problem normally s/w or h/w related? What are some suggestions for narrowing down the scope of the problem? Should I attempt an upgrade to Gibbon as my first course of action?

I recognize that it is difficult to solve this problem with the information given.

I haven't yet tried using CTRL-ESC, CTRL-ALT-ESC, and CTRL-ALT-BACKSPACE, and will attempt it the next time it occurs.

---

### Post by greenwom on 2007-11-17
I've got  a HP DV9000 that has the same problem.
I've trouble-shot allot of problems since becoming a Linux user but I can't find anything that would cause this.   Any one know what log to look into?  

I guess I'll just upgrade to Gusty and see if it fixes it....

---

### Post by mustbealennox on 2007-11-19
As a follow up to my own posting, it locked up again today and the CTRL-ALT-BACKSPACE, CTRL-ALT-ESC, and CTRL-ALT combinations have no effect.

greenworm, let me know if your upgrade solves the problem.

---

### Post by mustbealennox on 2007-12-03
The ALT-PRINTSCREEN + R-S-E-I-U-B keys don't allow me to shut down gracefully. When the system locks up, it appears to no longer receive any input from the mouse or keyboard.

After reading other posts with the "freeze" keyword, I thought it may be related to the driver for my video card, but this seems to be more serious than that.

Any other suggestions from the Ubuntu community?

---

### Post by konradsa on 2007-12-03
Does Alt + F2 and then "metacity --replace" make this problem disappear?

---

### Post by mustbealennox on 2007-12-21
When should those commands be run? When it locks up or now?

Could you explain what they do?

---

### Post by konradsa on 2007-12-21
You should run these commands before it locks up, and see if that reduces or eliminates the lockups.

---

### Post by Nano Geek on 2007-12-21
Before you try that though, do you have a Nvidia graphics card?
If so then please tell me what kind and what driver you are using?

---

### Post by mustbealennox on 2008-01-04
Thanks very much for your help.

Yes, its an Nvidia graphics card.

As an aside, how do I list which driver is being used for any particular device? After searching other threads, the nvidia driver appears to be listed in the xorg.conf file. But in general, is there a command that can be run to dump this info (eg. for a sound card, etc)?

```
lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
```

From my /etc/X11/xorg.conf file:
```
Section "Device"
        Identifier      "nVidia Corporation NV20 [GeForce3 Ti 200]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "PnP Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV20 [GeForce3 Ti 200]"
        Monitor         "PnP Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

---

### Post by Nano Geek on 2008-03-22
Well, I'm not really sure. The "nv" driver usually doesn't have that type of problem. 
It sounds like it could be overheating, but have you tried using Gutsy instead of Feisty yet?
I'd try that first.

---

