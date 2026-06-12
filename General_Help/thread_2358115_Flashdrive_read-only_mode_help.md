---
title: "Flashdrive read-only mode help"
date: 2017-04-09
forum: General Help
---

### Post by Camilia on 2017-04-09
Everytime I reinsert my flashdrive it is in read-only mode. In the past in terminal sudo Terminal>sudo hdparm -r0 /dev/sda worked. Now it doesn't work.

---

### Post by yancek on 2017-04-09
One common reason for that is if the filesystem gets corrupted and needs a filesystem check, fsck on the partition.
What type filesystem is it?  Do you use it just to store data?

---

### Post by Camilia on 2017-04-10
I just buy flash drives and use them. I don't format them. Occasionally I have erased and reformatted a flash drive with windows os on laptop. I have noticed the format is FAT 32. I basically have spread sheets with shopping expenses and budgeting saved on flashdrive. Plus some pictures.

Well to determine what type of file system the flash drive had I went into its properties and found that I can change the permission. So now it is fixed. It won't stay fixed for long though.

---

