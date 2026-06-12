---
title: "Ubuntu 14.04.2 display missing some characters"
date: 2015-04-23
forum: General Help
---

### Post by nvcnvn on 2015-04-23
I have post the question on askubuntu but no help, here is the link in case you want some rep [http://askubuntu.com/questions/612045/ubuntu-14-04-2-display-missing-some-characters](http://askubuntu.com/questions/612045/ubuntu-14-04-2-display-missing-some-characters)
Some time the text display missing some characters, its happen on a UI window or even the terminal text.
I have a screenshot here (for example Os type missing the number '64'): 
Here is my lspci output:

```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
```

---

### Post by dino99 on 2015-04-23
From the System Settings (from top right cog), tweak both 'Language Support' & 'Region & Language'
by tweaking, i mean to switch (temporaly) to some other setting (language) and validate the choice, then, after a logout/in,  switch back to your prefs. That should clean some wrong validation (possibly related to utf-8)

are you using one language for the system, and an other one for the keyboard ? (then possible conflict needing to report)

---

### Post by nvcnvn on 2015-04-23
Thanks you!
I tried that but the issue still remain. My ubuntu is a fresh new install and i use both English for the system and keyboard.
One thing to mention that the issue not happen all the time, after working with it for a while then the issue happen...restart make everything back to normal.

---

### Post by dino99 on 2015-04-23
Are logs having some usefull warnings/errors ?  (syslog/xorg.0.log)

---

### Post by Bucky Ball on 2015-04-24
*Thread moved to **General Help**.*

Hi. Please use default font/size/colour for posts and code tags for terminal output (please see the last link in my signature for how). Thanks and good luck. ;)

---

