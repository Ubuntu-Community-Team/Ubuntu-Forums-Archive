---
title: "Unable to resize unallocated partition space"
date: 2019-02-02
forum: General Help
---

### Post by testudo2 on 2019-02-02
I resized my Root partition (sbd5) to free up some additional space (57.13GB) for my Home partition, but I'm stuck increasing the size of the Home partition(sbd3) in gparted.  I can add the unallocated space back to sbd5,  but have no option to when trying to incorporate it to to the intended sbd3 partition.  I thought it needed to be adjacent and then i could just resize, adding the unallocated space to the partition.  But that doesn't seem to be the case.  Any advice is appreciated.

[ATTACH=CONFIG]282379[/ATTACH][ATTACH=CONFIG]282380[/ATTACH][ATTACH=CONFIG]282381[/ATTACH]

Cheers,
Testudo

---

### Post by CatKiller on 2019-02-02
Notice how sdb5 is enclosed within sdb2. You need to make that smaller too before the space is available to sdb3.

---

### Post by Impavidus on 2019-02-02
Note that it's sdb, not sbd.

You've got a old-fashioned mbr partitioning (nothing wrong with that), which has a limit of 4 primary partitions. You can get around that limit by making one of the primary partitions a container for some logical partitions. This container is your sdb2. To add your unallocated space to sdb3, you first have to move the left edge of sdb2 to the right.

BTW, that ntfs partition is so full that you can't add anything to it without suffering from insane fragmentation.

---

### Post by Mark Phelps on 2019-02-02
I've never seen a Windows partition that full -- so the first thing I would do is try some steps to free up some disk space in that partition.

Here are the steps:  
[http://www.tenforums.com/tutorials/3012-disk-cleanup-open-use-windows-10-a.html](http://www.tenforums.com/tutorials/3012-disk-cleanup-open-use-windows-10-a.html)
[http://winaero.com/blog/how-to-clean-up-winsxs-folder-in-windows-10/](http://winaero.com/blog/how-to-clean-up-winsxs-folder-in-windows-10/)

Also, the community Win10 Forums has the following suggestions:
[https://www.tenforums.com/tutorials/83441-free-up-drive-space-windows-10-a.html](https://www.tenforums.com/tutorials/83441-free-up-drive-space-windows-10-a.html)

IF those work well, you might not have to struggle with repartitioning.

Good Luck

---

### Post by testudo2 on 2019-02-02
> **Impavidus said:**
> Note that its' sdb, not sbd.

You've got a old-fashioned mbr partitioning (nothing wrong with that), which has a limit of 4 primary partitions. You can get around that limit by making one of the primary partitions a container for some logical partitions. This container is your sdb2. To add your unallocated space to sdb3, you first have to move the left edge of sdb2 to the right.

BTW, that ntfs partition is so full that you can't add anything to it without suffering from insane fragmentation.

Thanks for the advice and sorry for the typos on the drive names, temporary late night dyslexia.  Moving the unallocated space did the trick.  BTW, that stuffed Windows partition is just backup files that I've been migrating to Ubunutu. I don't plan on using Windows much, so it is not going to need any additional storage space.
[ATTACH=CONFIG]282390[/ATTACH]

---

### Post by Impavidus on 2019-02-03
Good.

Could you mark this thread as solved? Thread tools &#8594; mark as solved.

---

