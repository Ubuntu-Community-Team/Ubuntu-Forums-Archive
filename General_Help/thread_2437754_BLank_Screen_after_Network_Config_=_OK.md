---
title: "BLank Screen after Network Config = OK"
date: 2020-02-28
forum: General Help
---

### Post by grimdemeanor on 2020-02-28
hello,
I am running Ubuntu 18.04 LTS Server w/ KDE GUI on a dell poweredge t310 tower in UEIF installed in a RAID 1 Config on Dual 500gb WD black hard drives ,
 Recently after complete shutdown and restart, it will load ask for the password, the screen will scroll all the services starting with the green OK's, and normally the display will load after the network configuration loads in about 1m30s, however now after the network loads, the screen just goes blank and i have no option to log into the machine or anything at that point. On my other systems i can hit the left shift key on boot and access the recovery menu, however they dont load with UEIF or a boot encrypted password so when i attempt to press shift for the recovery menu it never loads and just contiunes the normal boot process until the blank screen issue. Any help on this issue would be great either a idea as to the casue of the problem or a way to load to the recovery mode other than the left shift or maybe its the timing of when the left shift is pressed i am not sure 
Thanks ahead of time

-Grim

---

### Post by CelticWarrior on 2020-02-29
I don't if it's the same with KDE but with Gnome we would use CTRL+ALT+F3 to get a TTY (CTRL+ALT+F7 to go back to the desktop).

If F3 doesn't work try others, F1, F2...

Once you get a TTY you can login. Before anything else install updates, reboot and try again. If the problem persists you need to troubleshoot KDE from the command line.

---

