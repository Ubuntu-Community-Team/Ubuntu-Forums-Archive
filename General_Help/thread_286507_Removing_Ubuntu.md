---
title: "Removing Ubuntu"
date: 2006-10-27
forum: General Help
---

### Post by razored on 2006-10-27
First off all, my primary HD has Windows XP on it and Ubuntu 6 on it. Recently, i've put in a second HD which also has Ubuntu 6 on it. I've been meaning to remove Ubuntu 6 from my first HD and make both of the HDs see each other in the OS Selection boot screen. Unfortunately, I suck at this kind of stuff... so how would I go about doing this? Big Thanks.

Here are my current settings :
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7439    59753736    7  HPFS/NTFS
/dev/hda2            7440       14299    55102950   83  Linux
/dev/hda3           14300       14593     2361555    5  Extended
/dev/hda5           14300       14593     2361523+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris
```

---

### Post by John.Michael.Kane on 2006-10-27
If you have the ubuntu live cd you can use the gparted program on it to delete the partition table on that drive.

---

### Post by razored on 2006-10-28
I used Gparted to delete the 2nd partition, then it the booter said Error 22, so i removed the third partition also, but it still says Error 22 just stays that way. What do I do now?

---

### Post by matt_risi on 2006-10-28
Looks like GRUB is on the MBR, anyone know how to reinstate the windows boot loader for this gentleman?

---

### Post by razored on 2006-10-28
Fixed it.. popped in my XP disc and went to recovery and typed in MBR and it's fixed :D

---

### Post by matt_risi on 2006-10-28
Wow, that was uncharacteristically easy. Good show.

---

