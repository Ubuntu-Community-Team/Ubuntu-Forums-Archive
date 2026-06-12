---
title: "Suspend mode broken / swapon-&gt;swapoff after reboot"
date: 2023-02-02
forum: General Help
---

### Post by iik71 on 2023-02-02
I have these two problems on my system and I am wondering if they are connected.
First I noticed that once my system goes to suspend or locked screen for a long time, the keyboard is blocked and does not type, or it types but I cannot use ENTER key which prevents me from login in to the system.
I disabled the locked screen and then I pushed my system to suspend. once returned from suspend mode, the cursor of the mouse was a square and any app i tried to start returned "failed to open". Additionally the folders', icon pictures and the wallpaper disappeared.

I assumed i have a problem with the swap space. checked with gparted. the swap was on swapoff status. i made it swapon but everytime i reboot the system it is again to swapoff.

these two seem like serious bugs but there is no good support from Ubuntu side to report such bugs. unfortunately.

anybody? good ideas?

---

### Post by MAFoElffen on 2023-02-02
Report the bug to launchpad.net. I think, as you described, the bug is already files as: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1970957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1970957)

---

