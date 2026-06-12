---
title: "Question regarding Ubuntu Installation and previous OS"
date: 2007-12-09
forum: General Help
---

### Post by amazingDentist on 2007-12-09
Hello and happy sunday.
This is my first post.
Glad to be here and I appreciate the mod support that ya'll do.

So....
I installed Ubuntu 7.10 using an ISO install disc.  I took no actions to delete or uninstall the previous OS, Windows Vista OS which has been plaguing my laptop right out of the box. :???:
My question is... Is it possible that I still have Windows Vista on my computer?
If so, i'd like to get rid of it once and for all.
What actions would I need to take to accomplish this?

Thanks.

- mike

---

### Post by dpar on 2007-12-09
Depends.....did you pick 'use entire disk' or whatever it says when you did the install??

Post the results of  > sudo fdisk -l

That's a small L

---

### Post by aysiu on 2007-12-09
Can you be more specific than *I took no actions to delete*?

When you got to the partitioning part of the installation, what did you select?

Also, can you post the output of this [terminal](http://www.psychocats.net/ubuntu/terminal) command? ```
sudo fdisk -l
```

---

### Post by amazingDentist on 2007-12-09
I selected 'Use Entire Disc'

The results for sudo fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x209b4b29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       21736   173050781+   7  HPFS/NTFS
/dev/sda3           21737       30042    66717945   83  Linux
/dev/sda4           30043       30401     2883667+   5  Extended
/dev/sda5           30043       30401     2883636   82  Linux swap / Solaris


Thanks for the expedient responses.

-mike

---

### Post by aysiu on 2007-12-09
*Use Entire Disc* should have erased your Vista installation, but I'm seeing an NTFS partition in there (/dev/sda2). That's weird.

---

### Post by anjilslaire on 2007-12-10
If that's a dell laptop that shipped with MediaDirect, that's what that  ntfs partition may be. It sits in a protected area of the drive, and the only sure way to remove it is to zero the drive. For more details, search the dell support subforum here for "media direct"

---

### Post by amazingDentist on 2007-12-10
It's a Toshiba A-215 Satelite

---

