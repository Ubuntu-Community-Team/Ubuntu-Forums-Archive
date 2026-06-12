---
title: "Boot problems after restore"
date: 2015-11-05
forum: General Help
---

### Post by keith46 on 2015-11-05
I had to replace a hard drive and did a bare metal restore from backup.  I only have one operating system on the drive (it's not a dual boot).  When I attempt to boot, I get a "no operating system found" message.  [COLOR=#333333][FONT=Lucida Grande]If I boot to a SuperGrub2 CD, I can see menu.lst at hd0,msdos2. Disks and Partitions detected shows Ubuntu at hd0,msdos1. When I attempt to load GRUB (at hd0/msdos1) from the SuperGrub2 menu I get the "invlaid signature" error. Any help is appreciated.[/FONT][/COLOR]

---

### Post by yancek on 2015-11-05
What release of Ubuntu are you using?  There hasn't been a menu.lst file for years, since the switch to Grub2 with version 9.10.  Google "boot repair ubuntu" and go to the site and download it and run it, selecting the option to "Create Bootinfo Summary" and post a link to it here.  It will give the information needed to advise.

---

