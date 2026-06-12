---
title: "Odd Resolution Problem"
date: 2007-09-18
forum: General Help
---

### Post by Malviolent on 2007-09-18
Hello, I have a 20.1" monitor with a native resolution of 1680x1050.  Using the nv driver I can use my native resolution; however, when I download nvidia's latest driver for my video card (a 6600) I get an out of range error whenever I try to use a resolution higher than 1440x900.  I've tried downloading the debian package, sudo apt-get install nvidia-glx, and envy.  Any help is greatly appreciated, thanks!

---

### Post by yabbadabbadont on 2007-09-18
Make sure that you have the correct values for the valid horizontal and vertical frequency ranges for your monitor and then manually update your /etc/X11/xorg.conf with them.  You will also probably have to force the binary nvidia driver to ignore the values returned by the monitor in its EDID information.  The nvidia driver is very conservative by default when it calculates valid video modes.  As an example, here is the relevant portion of my xorg.conf file:
```
Section "Device"
        Identifier      "nVidia Corporation NV25 [GeForce4 Ti 4200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"         "1"
        Option          "UseEDID"       "false"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-80
        DisplaySize     306 230
        Gamma           0.75 0.75 0.75
EndSection

```

---

### Post by Malviolent on 2007-09-21
thanks so much for the help.  I think it was the rejection of the monitor's EDID information that did the trick.

---

### Post by Malviolent on 2007-09-27
now I have another odd problem.  every time I restart my machine, my X server fails to start.  I get an error telling me about an API mismatch error.  I reinstall the driver and reconfigure my xserver and it will start again, but it will NOT start again simply off a reconfigure.  I have to  completely reinstall the driver.  Anyone?

---

