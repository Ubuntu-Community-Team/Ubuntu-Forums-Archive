---
title: "Beryl won't work..."
date: 2007-08-06
forum: General Help
---

### Post by eunixd on 2007-08-06
Is it possible to instally beryl with wubi? I tried various versions, but my screen gets lost and i have a problem with my x server. Any advice?

---

### Post by Romanus81 on 2007-08-06
Search these forums: [http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)
Wubi just installs Ubuntu on your system, after that it works the same as a normal ubuntu install.

---

### Post by Kralizec on 2007-08-06
What graphics card do you have?

```
lspci
```
in terminal should tell you. Look for the line that has "VGA compatible controller".

If you have an ATI card, you may need to take some extra steps to get it working.

---

### Post by eunixd on 2007-08-06
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

---

### Post by Kralizec on 2007-08-06
Ok, that should work without too much more effort...Look in your xorg.conf and report what driver is listed in your 'Device' section:

```

Section "Device"
        Identifier  "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        **Driver      "fglrx"**
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "DesktopSetup" "clone"
        BusID       "PCI:1:5:0"
EndSection

```

---

### Post by eunixd on 2007-08-06
um how do i open xorg.conf?

---

### Post by eunixd on 2007-08-06
Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

this is from etc/X11/xorg.conf

---

### Post by Kralizec on 2007-08-06
In terminal type 
```

gedit /etc/X11/xorg.conf

```
for now, since we only need to read it. If you want to edit it, you would have to add 'gksudo' in front of 'gedit', but for now all we want to do is look at it.

---

### Post by eunixd on 2007-08-06
Section "Device"
Identifier "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

this is from etc/X11/xorg.conf

---

### Post by Kralizec on 2007-08-06
Ok, then this how-to should help: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"); notice the page 2 and 3 links at the bottom.

If you have any problems or questions, feel free to ask.

---

### Post by eunixd on 2007-08-06
how do i make sure my desktop is updated?

---

### Post by Kralizec on 2007-08-06
Well if you've just installed Ubuntu, its likely that you're all up-to-date. However, to be sure, in a terminal do
```

sudo apt-get update

```

And then on your menu bar click System -> Administration -> Update Manager then check for updates, make sure they're all checked, and hit "Install Updates". If there aren't any there, then you're all updated.

---

