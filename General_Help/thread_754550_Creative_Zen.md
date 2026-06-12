---
title: "Creative Zen"
date: 2008-04-13
forum: General Help
---

### Post by estanton on 2008-04-13
I've been trying to load music up on my girlfriends Creative Zen Mp3 Player, generally it's pretty easy (just drag and drop) except it's only recognising half of the drive. For some reason even though it recognises that it's 1Gb it says there's only half a gig free, says half of it is already full but declines to show what the other half gig is being occupied by. Any suggestions?

---

### Post by dcast on 2008-04-13
Try clearing your trash, I always have this happen and the trash folder gets created on removable medias such as a USB memory stick and the folder is hidden and steals your memory from you.

---

### Post by estanton on 2008-04-13
That was my first thought too, I've noticed sometimes you have to go in and manually scrub the files from trash as well. Unfortunately that isn't doing the trick.

---

### Post by estanton on 2008-04-14
I've noticed that in Gpartedr the Zen shows up as /dev/sdb but as only 243 Mb and unallocated... hmmm

---

### Post by bapoumba on 2008-04-15
I clear the trash from the command line and get all the space available again.

---

### Post by estanton on 2008-04-16
hmmm clearing from the command line didn't work unfortunately, i think the problem here is a little deeper then that. fdisk -l yields > Note: sector size is 2048 (not 512)

Disk /dev/sda: 1042 MB, 1042939904 bytes
218 heads, 32 sectors/track, 73 cylinders
Units = cylinders of 6976 * 2048 = 14286848 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          73     1018432    e  W95 FAT16 (LBA)

and fdisk /dev/sda simply yields> Note: sector size is 2048 (not 512)


---

