---
title: "Desktop doesn't load after log in."
date: 2008-03-11
forum: General Help
---

### Post by obievil on 2008-03-11
I'm really new to this but I think I've learned quiet a bit for a newbie. however I am having one slight problem, one that i've investigated and can't seem to put my finger on. 
I can log in with ATI card, but the desktop never displays. 
here are snippets from my log file

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found

(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
 
```

now I'm fairly certain that most of those aren't important. 

however I checked my xorg.conf file and found this 
```

Section "Device"
        Identifier  "Failsafe Device"
        Driver      "ati"
        VendorName  "ATI"
        BoardName   "ATI Radeon (fglrx)"
        Option      "MergedFB" "off"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"

 #
        Identifier  "device1"
        Driver      "ati"
        VendorName  "ATI"
        BoardName   "ATI Radeon (fglrx)"
        Option      "MergedFB" "off"
        BusID       "PCI:3:0:1"
EndSection

```

I tried commenting out the bottom one but it forced the system to boot into low graphics mode. 

I'm at a bit of a loss, 
any help would be appericated.

---

### Post by obievil on 2008-03-12
I really need help?
anyway?
Bump

---

