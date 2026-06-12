---
title: "uninstall trillian"
date: 2014-11-23
forum: General Help
---

### Post by tuxbonewits.com on 2014-11-23
Well, I screwed up and installed Trillian 1.2.0.4 
I double clicked on a .deb package and 
the Ubuntu Software Center started and installed it

now I cannot get rid of it.

Synaptic Package Manager does not see it.
Ubuntu Software Center does not see it
apt-get purge didn't do anything
it runs on startup

How do I remove it?

I'll appriciate any help on this,

[email]tux@bonewits.com[/email]
===================================================

HP Pavillion g7 - 2269wm
AMD Quad-Core A8-4500M Accelerated Processor
17.3" diagonal HD+ BrightView LED Display
Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]
Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
500 GB HDD
DVD A DS8A9SH
6144MB DDR3 SDRAM
DVD Optical Drive
20140804 - Ubuntu 14.04.1 LTS Trusty Tahr OS

---

### Post by oldos2er on 2014-11-23
Try ```
sudo dpkg -r trillian
``` If it fails please post the entire output from that command here.

---

### Post by deadflowr on 2014-11-23
> **oldos2er said:**
> Try ```
sudo dpkg -r trillian
``` If it fails please post the entire output from that command here.

You might also try something like
```
dpkg -l trillian*
```
which should list the full package name with version number if that is a part of the package name.
Which might be why it isn't being found by apt...

---

### Post by tuxbonewits.com on 2014-11-27
Thank you, removed it :)

---

