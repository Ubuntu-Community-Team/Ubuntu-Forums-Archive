---
title: "Kubuntu 20.04 tearing with intel card - fix"
date: 2020-05-22
forum: General Help
---

### Post by maestrobwh1 on 2020-05-22
I was seeing a lot of flickering and tearing in KDE on two different machines and one machine, the LCD keys also did not work and I remembered some various "fixes" for the issues.  One I already posted for the brightness keys because it was an issue in 18.04 and still is in 20.04 for all flavors for a Toshiba machine I have.  The "tearing" happens on both machines running Kubuntu Fossa's version of Plasma.

create this file

/usr/share/X11/xorg.conf.d/20-intel.conf

Paste this in it

```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
	Option      "AccelMethod" "uxa"
        BusID       "PCI:0:2:0"
EndSection
```

---

