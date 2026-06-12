---
title: "Cannot find WiFi"
date: 2013-09-09
forum: General Help
---

### Post by smb140p on 2013-09-09
Hi,

Am using HP Mini 110. Recently downloaded Lubuntu 13.04 and am running it off live USB. Hardware switch on my laptop is on, but can't find any networks, when I click on the wireless icon, enable networking is ticked, there's a greyed out unclickable information below, and below that is "edit". I'm an absolute beginner to Linux so I'd appreciate any help to get it working. Let me know if there's any information I missed out.. I do not know what my wireless card is, but should be the standard.

Evan

---

### Post by varunendra on 2013-09-09
Please open a terminal (Ctrl+Alt+T), and post the output of following commands :
```
lspci -nnk | grep -iA2 net
rfkill list all
```

**EDIT:**
Nevermind with the first command. Based on outputs from your [previous]("http://ubuntuforums.org/showthread.php?t=2037656") thread, you seem to have a BCM4312 card. Accordingly, please download "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download)

Copy it to your Ubuntu 13.04 laptop and double-click to install. You may have to purge the proprietary driver if it is installed -
```
sudo apt-get purge bcmwl-kernel-source
```

Then do a reboot or -
```
sudo modprobe -v b43
```
..and enjoy your wireless. :)

---

