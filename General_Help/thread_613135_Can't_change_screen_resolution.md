---
title: "Can't change screen resolution"
date: 2007-11-14
forum: General Help
---

### Post by ylinux on 2007-11-14
Hi guys, I'm new to Linux. I just install xubuntu 7.10 on a Pentium II 400MHz machine and am trying to get it running at native res 1280x1024. 

It is currently running at 1024x768 but when I check in the display settings, this option is not available - I only see 'Default' (current setting), 800x600, 640x480. 

If I change the resolution to 800x600, there is no way to get back into 1024x768. I find all this strange because the splash screen before the login screen appears at 1280x1024 :confused:

---

### Post by mikewhatever on 2007-11-14
Go to Applications>Accessories>Terminal, past in the following and hit enter.

> cat /etc/X11/xorg.conf

Please post the resolutions section from the bottom of the file.

---

### Post by ylinux on 2007-11-14
> **mikewhatever said:**
> Go to Applications>Accessories>Terminal, past in the following and hit enter.



Please post the resolutions section from the bottom of the file.

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "CY765"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x640" "640x480" "640x400"
        EndSubSection
EndSection

---

### Post by ylinux on 2007-11-14
Anyone?

---

### Post by sstalpers on 2007-11-16
I am having the same problem on my old Sony Vaio PCG-FX105K (graphics: intel 815EM chipset) running Xubuntu 7.10. I got the screen back to 1028x786 by running ```
sudo dpkg-reconfigure xserver-xorg
```The Display Settings still does not list 1028x786. I'm just glad I got it back at its highest resolution!

---

### Post by ylinux on 2007-11-16
I tried doing ```
sudo dpkg-reconfigure xserver-xorg
```

And I got this
```

FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071116182010
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
```

---

### Post by froy02 on 2007-11-17
Go to Systems menu, choose Administration then Screen and graphics.  Check to make sure that your graphics card the one being used and that your monitor is the one selected. If not, select it and you'll be able to select the resolution that your monitor is capable of displaying. 

note; YOU MAY HAVE TO RE-START FOR THE SETTING TO TAKE EFFECT.

Froy

---

