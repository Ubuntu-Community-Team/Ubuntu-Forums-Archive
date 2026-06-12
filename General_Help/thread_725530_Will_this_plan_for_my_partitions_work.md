---
title: "Will this plan for my partitions work?"
date: 2008-03-15
forum: General Help
---

### Post by dorkdork777 on 2008-03-15
I've decided to try my hand at a few more Linux distros other than Ubuntu; namely Fedora and openSUSE. But I'll need to repartition to install them, and my plan for partitions needs changing. So, will this work?

Part. #1 - Windows (75 GB)

Part. #2 - File storage (100 GB)

Part. #3 - Linux swap (1 GB)

Part. #4 - Extended (74 GB)

----Part #5 - boot (500 MB)

----Part #6 - home (all distros) (30 GB)

----Part #7 - Ubuntu install (15 GB)

----Part #8 - Fedora install (15 GB)

----Part #9 - openSUSE install (15 GB)


The main things I'd like to question are the 'home' and 'boot' partitions. Will a single 'home' directory work across all distros? And if all my distros see the boot partition as the location of GRUB, will that mean that all kernel updates for all distros get added to that one GRUB menu? Plus, which file system is best for the boot partition? ext2, ntfs, FAT32, etc.

Thanks a lot! :)

---

### Post by Oldsoldier2003 on 2008-03-15
> **dorkdork777 said:**
> I've decided to try my hand at a few more Linux distros other than Ubuntu; namely Fedora and openSUSE. But I'll need to repartition to install them, and my plan for partitions needs changing. So, will this work?

Part. #1 - Windows (75 GB)

Part. #2 - File storage (100 GB)

Part. #3 - Linux swap (1 GB)

Part. #4 - Extended (74 GB)

----Part #5 - boot (500 MB)

----Part #6 - home (all distros) (30 GB)

----Part #7 - Ubuntu install (15 GB)

----Part #8 - Fedora install (15 GB)

----Part #9 - openSUSE install (15 GB)


The main things I'd like to question are the 'home' and 'boot' partitions. Will a single 'home' directory work across all distros? And if all my distros see the boot partition as the location of GRUB, will that mean that all kernel updates for all distros get added to that one GRUB menu? Plus, which file system is best for the boot partition? ext2, ntfs, FAT32, etc.

Thanks a lot! :)

some distros wont play nicely with a separate  /boot . Another idea is to make sure you use a differen tusername for each distro, so you wont have configuration issues.

---

### Post by dorkdork777 on 2008-03-15
But doesn't that kinda defeat the point of having the seperate /home? Being able to share configurations between distros?

---

### Post by Shazaam on 2008-03-15
Shared /home..........
Yes it COULD work but you run the risk of trashing files in your /home directory by conflicting distro configuration files. Since you are going to have a separate data partition making a shared home is unneeded IMHO. I give different distro's 20gigs (overkill) and all but one use less than 5gigs. That one is Ubuntu which has all of my music and pictures. I point the other distro's to it.

---

### Post by PapaNerd on 2008-03-15
If you were to set up a small /home directory for each linux OS (for the hidden files and sub-directories), then you could create a link to a common home sub-directory somewhere else (like on your data partition) from the /home in each distro.  That would isolate the config files, but let you work on common documents across each OS.

---

### Post by dorkdork777 on 2008-03-15
OK, so the shared home is out. Thanks to everyone who replied! Can anyone confirm that Fedora or openSUSE do/ do not play nice with a seperate /boot?

---

### Post by louieb on 2008-03-15
> **dorkdork777 said:**
> ... Can anyone confirm that Fedora or openSUSE do/ do not play nice with a seperate /boot?

Sharing a /boot partition is a bad idea. Personal experience sharing a /boot partition between Fedora and Ubuntu  - found out come kernel update time /boot/grub/menu.lst  got all messed up.

Look at Herman's explanation of chainloading or using the configfile option. That what I use and they works great.  [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

