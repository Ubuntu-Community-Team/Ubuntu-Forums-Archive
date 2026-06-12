---
title: "Screwy problem with MSI-FM2-A55M-E33 + A4-5300: freezes up 12.04"
date: 2012-11-11
forum: General Help
---

### Post by kodb on 2012-11-11
All,
I just swapped out a working 12.04.1 system  (32bit) to a new box with the MSI-FM2-A55M-E33 board plus a A4-5300 cpu and 8G of Kingston DDR3 1600 memory.  The machine boots and will bring up the login screen and I can login but then if I do anything at all once logged in it freezes up the desktop.  If I go to tty I can run anything without problem in the command line so I am assuming this is probably an xserver or gpu related issue with the integrated gpu.  Has anyone seen anything like this and can anyone point me in the direction of a fix?  If not then I'll have to reswap out the MB/CPU and go back to the older Athlon x2 245 I was running successfully.
Thanks,
Bob

---

### Post by cariboo on 2012-11-11
> **kodb said:**
> All,
I just swapped out a working 12.04.1 system  (32bit) to a new box with the MSI-FM2-A55M-E33 board plus a A4-5300 cpu and 8G of Kingston DDR3 1600 memory.  The machine boots and will bring up the login screen and I can login but then if I do anything at all once logged in it freezes up the desktop.  If I go to tty I can run anything without problem in the command line so I am assuming this is probably an xserver or gpu related issue with the integrated gpu.  Has anyone seen anything like this and can anyone point me in the direction of a fix?  If not then I'll have to reswap out the MB/CPU and go back to the older Athlon x2 245 I was running successfully.
Thanks,
Bob

Which graphics driver are you using?

---

### Post by kodb on 2012-11-11
Cariboo907-
Not exactly sure because in the interim  (before I saw your reply),I went ahead and added the xorg-edgers ppa (figuring that it had to be an issue with the A4-5300 gpu and the xorg files)and did a dist-upgrade which upgraded all the xorg drivers and bumped the kernel to a 3.5.x version.
I now have a working system but am going to have to see if the "advanced" kernel screws up anything else for me.    Stand by for further updates
Bob

---

