---
title: "Empty partition showing 10.9 Gb in use ????"
date: 2016-08-27
forum: General Help
---

### Post by raleigh3 on 2016-08-27
My sda1 partition is empty with no files or O.S.

Yet Gparted says it is using 10.9 Gb.

That makes no sense especially when Clonezilla spends a lot of time making an image of a empty partition.

Any explanation... a plasmoid ?? :-)

---

### Post by sudodus on 2016-08-27
How big is the partition? What file system is there?

A small percentage of the partition will be used to manage the file system, and in huge partitions, that small percentage can be several gigabytes.

---

### Post by Bucky Ball on 2016-08-27
> **sudodus said:**
> How big is the partition? What file system is there?

A small percentage of the partition will be used to manage the file system, and in huge partitions, that small percentage can be several gigabytes.

^^^
This.

Yes, Clonezilla does clone the whole partition, so shrink the partition. ;) Sounds like the bit you want probably only takes up a fraction of the partition by the fact that empty space is a problem. If this is the situation, shrink the partition so you have about 10Gb free space in the partition as 'headroom' (size of that up to you, though, but I like to play too safe) then clone to a partition the same size or bigger, but you probably know that. 

Good luck.

PS: If it's a Win partition you are wanting or needing to shrink, run a defragmentation app three or four times, preferably not the in-built Win one, before shrinking. If a big partition with a lot of data you'll gain some free space.

---

### Post by raleigh3 on 2016-08-27
Partition is ext3 and size is 681 Gb.

So, about 2% is being used.

I guess it is reserved space.

I could shrink the partition, but the new larger partition would still reserve 2% of the space.

---

### Post by sudodus on 2016-08-28
Yes, that is how it works.

---

### Post by SeijiSensei on 2016-08-28
You can adjust the size of the reserved area when formatting.  See the discussion of the "-m" parameter in "man mke2fs".  The default is five percent of the available disk space.

---

### Post by oldfred on 2016-08-28
The reserved space was back when drives were a lot smaller.
If a data only partition or if very large, you may not need the full 5%. But you still are responsible for maintaining system and not trying to use system when no space is left.

 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m). The -l lists parameters.
See man tune2fs
sudo tune2fs -l /dev/sdXY

---

### Post by raleigh3 on 2016-08-28
I used

> sudo tune2fs -m1 /dev/sda1 

No change in reserved space, it still uses 1.6 %. ??

I realize that some space is required for bad sectors, but 10.9 Gb is ridiculous.

Have a great evening.



                        [FONT=monospace][SIZE=4][B][COLOR=#000000]
[/COLOR][/B][/SIZE][/FONT]

---

### Post by oldfred on 2016-08-28
I have not used tune2fs, but man page make it look like a space after the parameter or -m 1

---

### Post by sudodus on 2016-08-29
We see not only (or maybe not at all) the reserved space, but the space for the administration of the file system, tables of *inodes* and blocks to connect each file name and file content, and directory name to the location in the memory space, plus for the journaling, which is a kind of backup system, that helps fixing minor errors in the file system.

If you search the internet for **ext4 overhead** you will find several informative links, for example:

[disk-space-overhead-in-ext4](https://serverfault.com/questions/282317/disk-space-overhead-in-ext4)

> I don't know if it applies to you, but just in case: most of the time the huge majority of the apparent overhead of ext2/3/4 will be due to the default significant amount of reserved blocks for root. Make sure you specify -m 0 (or 1) to mkfs.ext4 when creating the filesystem or to tune2fs if adjusting it afterwards. The default is 5, which stands for 5% of total blocks and can be excessive in most cases.

> Difficult question to answer this as the amount of DATA space would vary with the number of files, their size, ACLs, Root reserved space, blocksize etc. There is not really a easily fixed answer to this question.

> The most significant overhead comes from the **inode tables**, so it obviously depends on how many inodes you allocate. With the default options, every 128mb of disk gets 2 mb ( 8192 x 256 bytes each ) of inodes, or **1.6% overhead**.

---

### Post by raleigh3 on 2016-08-30
Thanks for the info.

---

### Post by sudodus on 2016-08-31
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by raleigh3 on 2016-09-03
I used sudo tune2fs -m 0 /dev/sda1, but there was no change in space used.

---

