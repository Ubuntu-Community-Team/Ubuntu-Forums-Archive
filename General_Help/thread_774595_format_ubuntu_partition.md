---
title: "format ubuntu partition"
date: 2008-04-29
forum: General Help
---

### Post by AJS302 on 2008-04-29
recently i have been dual booting xp and ubuntu 7.10 but now i want to get rid of the ubuntu partition but i can't format it from windows because it doesn't recognise it. is there anyway i can format it from windows or do i need to do something else?

thanks

---

### Post by GCoffee on 2008-04-29
If you installed ubuntu via live cd you can use gparted on the live cd to format or remove the partiton...

Be warned though, when I removed my openSUSE 10.3 partition windows didn't boot until I installed ubuntu... Grub got messed up, probably solved in the bios but I can't be sure.

---

### Post by ibutho on 2008-04-29
You can use a small live cd such as [PartedMagic]("http://www.partedmagic.com") to remove the Linux partitions. You also need to restore the Windows bootloader which can be done using [Super Grub Disk]("http://www.supergrubdisk.org/").

---

