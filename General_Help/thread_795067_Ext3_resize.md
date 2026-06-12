---
title: "Ext3 resize"
date: 2008-05-15
forum: General Help
---

### Post by awais_rauf on 2008-05-15
A newbie question......

I am a new ubuntu Hardy Herson user. I resized the ext3 partition by adding space from NTFS partition in front of it. Now when i boot ubuntu it says fsck needs to be done and shows alot of sector relocation to be done. I ran fsck from knoppix and now ubuntu is ok. Now when i check my disk space the partition has increased in size but all the space to has been filled up and only arround 600 mb left free.

---

### Post by tribaal on 2008-05-15
Normally fdisk should do the work on its own, you should only let it finish.
Maybe you have a different problem however, what exactly does fdisk say when you boot up?

- Trib'

---

### Post by awais_rauf on 2008-05-15
Thanks for the reply.

 I ran fsck from knoppix and ubuntu is fine now but all the disk space that i added somehow has got filled up and only arround 600 mb is left. Can you please explain how can i reclaim the free space.

---

### Post by az on 2008-05-15
Are you sure that the filesystem is resized too?  You may have increase the size of the partition, but the filesystem may still be small.  You can resize the filesystem to use all of the free space on the partition.

---

### Post by tribaal on 2008-05-15
After a little investigation, here is [a nice step-by-step tutorial]("http://www.howtoforge.com/linux_resizing_ext3_partitions_p2") on how to resize an ext3 filesystem.

Hope this helps.

- Trib'

---

### Post by awais_rauf on 2008-05-16
No i just resized the partition. I didnt know if filesystem had to be separately resized (as it is not so in windows).

---

### Post by bingoUV on 2008-05-16
What method did you use to resize your partition? 
1. gparted
2. qtparted
3. commercial tool (maybe from windows)
4. parted command line
5. fdisk
6. other

gparted and qtparted will resize both partition and filesystem in tandem (by default, maybe you can coerce them to do otherwise).

---

### Post by awais_rauf on 2008-05-16
I used Paragon disk manager a W32 partitioning utility to resize partition.

---

### Post by awais_rauf on 2008-05-17
Can someone please tell me how to resize the filesystem after resizing the partition?

---

### Post by bingoUV on 2008-05-19
From a live CD, 
```

sudo resize2fs <device> 

```

This will resize the filesystem to the size of the partition.

---

