---
title: "Unable to extend root partition"
date: 2018-12-01
forum: General Help
---

### Post by vtolenti89 on 2018-12-01
Hello there ):P

This is my first post in here. I have recently purchased a new laptop and installed windows 10 along with ubuntu (I am quite new to the latter).
After installing a few apps in Ubuntu I noticed I was running out of space in the root partition and tried to extend it through a Gparted being run from a live usb.
I cannot understand why I cannot extend the root partition to the rest of the unallocated space. The Home partition though can be extended.

[ATTACH=CONFIG]281836[/ATTACH]

I appreciate any help. 

Thanks!

---

### Post by CatKiller on 2018-12-01
You can't make your / partition bigger because your /home partition is between the / partition and the unallocated space. You can see it in the layout diagram in the screenshot you posted.

You need to move the startpoint of the sda7 partition to the right before you can move the endpoint of sda6 to the right.

---

### Post by vtolenti89 on 2018-12-01
Never mind, I managed to move it :)

---

### Post by cmcanulty on 2018-12-01
You have to run a live version from either a DVD or flash drive then unmount the partitions and resize. Be careful to backup first in case of a mistake. You can't resize a mounted partition.

---

### Post by vtolenti89 on 2018-12-01
Thank you all! I managed to expand the partition after moving the free space some slots.

---

