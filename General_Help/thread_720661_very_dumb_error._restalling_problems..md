---
title: "very dumb error. restalling problems."
date: 2008-03-10
forum: General Help
---

### Post by shotty on 2008-03-10
alright, i had recently installed ubuntu 7.10 gutsy gibbon, and i had problems installing it the first time, but i was being a retard and was trying to expand the partition for the ubuntu OS while, vista is running on another partition. (dual-boot) accidentally deleted the partition with ubuntu on it, now i was trying to expand the partition to install ultimate edition (ubuntusoftware.info) and well grub got deleted along with the operating system, so instead of dual booting im just goin to try to get rid of grub and ubuntu and install it on another system.
it tries to start grub up, when obviously it isnt there so i cant log in to vista at all. it gives me error #17 and wont go any further. is there an easy fix to get GRUB loading thing off my computer?

---

### Post by Rocket2DMn on 2008-03-10
If you're trying to get back into windows, load from the windows cd, enter the recovery console and run
```
fixmbr
```
If that doesn't work or you want to get GRUB working again, here is how: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
At the moment, that help site seems to be unavailable, so here is the google cache: [http://209.85.173.104/search?q=cache:iEE-Xfyc0mQJ:https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows&hl=en&ct=clnk&cd=1&gl=us](http://209.85.173.104/search?q=cache:iEE-Xfyc0mQJ:https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows&hl=en&ct=clnk&cd=1&gl=us)
It's OK to overwrite the windows bootloader.

---

