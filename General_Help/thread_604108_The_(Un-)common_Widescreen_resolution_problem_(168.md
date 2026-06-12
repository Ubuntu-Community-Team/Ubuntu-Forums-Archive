---
title: "The (Un-)common Widescreen resolution problem (1680x1050)"
date: 2007-11-05
forum: General Help
---

### Post by faberoo on 2007-11-05
Hello:

Thanks in advance for your help!

I have a widescreen LCD monitor intended for 1680x1050 display. I have just installed Suse 10.3 (KDE) and an Intel i845 graphics card installed. Using all the 'tricks' of the trade (915resolution, changing xorg.conf, updated intel drivers), and nothing seems to work. I get a crisp image, but the picture does not fill the entire wide screen. Does anyone have any tips which might help? Here is some config code:

>#915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3de
Mode Table Entries: 18

Mode 30 : 1680x1050, 8 bits/pixel
Mode 32 : 1680x1050, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 1680x1050, 16 bits/pixel
Mode 43 : 1680x1050, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 1680x1050, 32 bits/pixel
Mode 52 : 1680x1050, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


My xorg.conf file:

Section "Monitor"
  DisplaySize  1680 1050
  HorizSync    30-66
  Identifier   "Monitor[0]"
  ModelName    "1680X1050@60HZ"
  Option       "DPMS"
  VendorName   "--> LCD"
  VertRefresh  50-61
  Modeline      "1680x1050" 123.0 1680 1784 1960 2240 1050 1053 1059 1089
EndSection


Section "Screen"
  DefaultDepth 24

  SubSection "Display"

    Depth      24
    Modes      "1680x1050"
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

Section "Device"
  BoardName    "i845"
  BusID        "0:2:0"
  Driver       "intel"
  Identifier   "Device[0]"
  Option       "XVideo"
  Screen       0
  VendorName   "Intel"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection



(All the values for mode I took from /var/log/Xorg.0.log)


Thanks so much! This is driving me up the wall!

---

### Post by jpeddicord on 2007-11-06
That is weird. As long as you are using the Intel driver and not "i810", you shouldn't need 915resolution, that's for sure. Try running the following in a terminal and see if you get better results after going through it:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by faberoo on 2007-11-07
In fact, I'm  using OpenSuse, so there's no automatic dpkg feature. Are you suggesting I reinstall xserver? (I'm not quite clear on what dpkg-reconfigure xserver-xorg does - does it set back to defaults? Reconfigures? If so, to what? Or does it update xserver to its latest version?)

Thank you!

---

### Post by dcstar on 2007-11-07
> **faberoo said:**
> In fact, I'm  using OpenSuse, so there's no automatic dpkg feature. Are you suggesting I reinstall xserver? (I'm not quite clear on what dpkg-reconfigure xserver-xorg does - does it set back to defaults? Reconfigures? If so, to what? Or does it update xserver to its latest version?)

Thank you!

One would suggest that asking for an OpenSuse solution in an Ubuntu forum is a waste of time for all involved. This is** not** a general Linux support forum, it is a general** Ubuntu** support forum.

To answer your question, in Ubuntu (and other Debian distros), it creates a new xorg.conf file. Since you do not apparently have this same tool, this information may not be of any use whatsoever to you.

---

### Post by faberoo on 2007-11-07
My question is not a distro-specific question, since it is Xorg-based, and I posted on this Ubuntu site because I had the exact same problem when I was using Ubuntu. Either way each distro automatically generates xorg.conf files is incorrect, for me. I have found many other threads on this topic on this forum, and thought it appropriate to add.  I am sure countless others have my problem as well. I am not looking to steal time on an inappropriate forum. I think finding an answer to this problem would benefit people with this problem, regardless of flavor of linux. I can only hope the helpful opensource community feels the same way.

---

