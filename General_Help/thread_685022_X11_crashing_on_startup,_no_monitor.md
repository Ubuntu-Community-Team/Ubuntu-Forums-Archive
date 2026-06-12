---
title: "X11 crashing on startup, no monitor"
date: 2008-02-01
forum: General Help
---

### Post by jSpazzoid on 2008-02-01
Hello everyone, 
I've just started to have trouble with X11 (fatal error on bootup)  when I tried to switch to a second monitor that wasn't plugged in. This was not for dual monitors but to switch to another monitor. Now I think that X11 is looking for a monitor that's not there, but I'm new to this and probably wrong. This is the first time I've had an error with X11 other then getting stuck at one resolution and having no status bar for the bootsplash.
 
Here's what my xorg.conf file says:

```
Section "Device"
             Identifier             "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
             Boardname          "ati"
             Busid                   "PCI:1:5:0"
             Driver                  "fglrx"
             Screen   0
EndSection

Section "Monitor"
            Identifier              "Generic Monitor"
            Vendorname        "Plug 'n' Play"
            Modelname          "Plug 'n' Play"
    modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync 
            Gamma     1.0
EndSection

Section "Screen"
             Identifier             "Default Screen"
             Device                 "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
             Monitor               "Generic Monitor"
            Defaultdepth       24
            SubSection          "Display"
                         Depth     24
                         Virtual     640              480
                         Modes                       "640x480@60"
           EndSubSection
EndSection

Section "ServerLayout"
           Identifier             "Default Layout"
     screen 0 "screen1" 0 0 
           Inputdevice         "Generic Keyboard"
           Inputdevice         "Configured Mouse"
           Inputdevice         "Synaptics Touchpad"
EndSection
Section "Module"
          Load                     "glx"
          Load                     "dbe"
          Load                     "v41"
EndSection
Section "Extensions"
          Option                  "Composite"        "1"
EndSection
Section "device" #
            Identifier            "device1"
            Boardname         "ati"
            Busid                  "PCI:1:5:0"
            Driver                 "fglrx"
            Screen     1
EndSection
Section "screen" #
            Identifier            "screen1"
            Device                "device1"
            Defaultdepth      24
            Monitor              "monitor1"
EndSection
Section "monitor" # 
           Identifier            "monitor1"
           Gamma      1.0
EndSection
Section "ServerFlags"
EndSection 
```

---

### Post by jleaker01z on 2008-02-01
Try running: sudo dpkg-reconfigure -phigh xserver-xorg

This will reconfigure your X server and should install your new monitor for you.

---

### Post by jSpazzoid on 2008-02-01
ok, i tried the command and it brought up the configuration utility. but when i try to hit ok it exits and gives me the following message.

xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080201192041

---

### Post by jSpazzoid on 2008-02-01
Also, I am not trying to get the new monitor working at this point, just the original monitor, but I think that the dpkg-reconfigure command would work for that too, except for the error I got.

---

