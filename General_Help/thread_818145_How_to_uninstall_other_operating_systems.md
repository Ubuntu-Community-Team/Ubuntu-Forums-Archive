---
title: "How to uninstall other operating systems"
date: 2008-06-04
forum: General Help
---

### Post by edno99 on 2008-06-04
Hello

I've just installed the latest version of ubuntu on an old pc, but I now want to uninstall the dodgy copy of windows on it to free up some space. I also installed a version of ubuntu server and would like to uninstall that too. 

Can I do this from the desktop version of ubuntu, and if so, how? The XP thats on the machine is corrupt so I can't get into the OS to uninstall from there, or format the disks :(

Thanks for any advice!

---

### Post by joshedmonds on 2008-06-04
In Ubuntu you can mount the other drives/partitions if you need to retrieve files from them, otherwise install a package called GParted which gives you a graphical partition manager (System->Administration->Partition Editor) so you can format and re-use that hard-drive space

---

### Post by spanish07 on 2008-06-04
well i am quite new at this but after looking through some sites it seems you can do it using fdisk on windows and going thru some steps but i do remember the ubuntu setup being real quick. I suggest you just run through the setup again and just write over the whole partition.

---

### Post by mikewhatever on 2008-06-04
There is no uninstall button for an OS. You should simply delete or format the partitions those OSs reside on using Gparted. It can be done from Ubuntu, provided the partitions are unmounted, and if Ubuntu desktop was the last OS installed, there should be no issues with boot loader.

---

### Post by edno99 on 2008-06-04
Does mounting mean I can get the xp data (like the music files and photos etc.) off the disk before formatting it? That would be amazing if I could :)

---

### Post by mikewhatever on 2008-06-04
> **edno99 said:**
> Does mounting mean I can get the xp data (like the music files and photos etc.) off the disk before formatting it? That would be amazing if I could :)

Yes, sort of. Mounting makes a partition accessible to the OS so that you can browse and manage it's directories and files. Current Ubuntu releases have XP file system (ntfs) access enabled by default.

---

