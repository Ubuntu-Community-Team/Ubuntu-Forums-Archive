---
title: "ubuntu 13.04 kernel panic not syncing errorcode=0x00000100"
date: 2013-07-02
forum: General Help
---

### Post by guilhermemtr on 2013-07-02
So today i was using the terminal in my pc and suddenly, it started saying that it couldn't find any program, even ls it couldn't find, so i thought that reboot could fix that. however when i rebooted it just started with kernel panic ( not syncing : Attempted to kill init), errorcode=0x00000100. if i had an hdd i would reinstall it, however i have an ssd, so i didn't wanted to just reinstall it. So i tried with a live cd try to figure out what was happening. i tried to chroot to usual / mount point, however i got an error, just like i was getting before the reboot, so when i do chroot to the disk, i get an error saying that /bin/bash hasn't been found. now i have no idea how to solve it.
any help would be appreciated

---

### Post by dino99 on 2013-07-02
no worry, its often a memory race issue while loading the kernel; simply retry. If that issue persist, then try with some boot option, and last, rise a report.

---

