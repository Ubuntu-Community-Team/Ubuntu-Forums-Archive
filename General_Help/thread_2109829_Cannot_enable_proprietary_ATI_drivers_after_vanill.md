---
title: "Cannot enable proprietary ATI drivers after vanilla install"
date: 2013-01-28
forum: General Help
---

### Post by Tylerofl on 2013-01-28
I installed 12.10 on my desktop, which has a Radeon HD 6870 GPU. Installation goes without an issue, and the OS works great. However, when I try to enable the fglrx proprietary drivers (this also happens using fglrx-updates) from the Software Sources menu and reboot, I get a blank screen with a blinking cursor and never make it past there. I have to go into root in recovery mode and remove the drivers. I thought that maybe I messed something up in my initial configuration, so I reinstalled 12.10 from scratch, went in to enable the drivers immediately after running updates, and the same thing happened. Is there some issue with Xorg and the ATI drivers right now?

EDIT: Grammar, clarification on fglrx-updates

---

### Post by Tylerofl on 2013-01-28
UPDATE: Yes, it's indeed a problem with the current driver. This has been going on since October? Really? :-x

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1069199](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1069199)

---

