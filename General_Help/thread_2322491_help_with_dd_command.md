---
title: "help with dd command"
date: 2016-04-28
forum: General Help
---

### Post by Old Jimma on 2016-04-28
Hi Ubuntu Community:

I have a 3TB hard drive that has several partitions.

I need to use the dd command to copy everything that is on one (and only one of those partitions of those partitions to another 3TB drive that has only 1 partition.

Can anybody please help me with how to do that?

Thanks!
Old Jimma from the Old Country

---

### Post by him610 on 2016-04-28
You might consider using clonezilla instead of dd.
You can read about it here....
[http://clonezilla.org/]("http://clonezilla.org/")

---

### Post by 1clue on 2016-04-28
you might not find dd to be the best tool for that. Variations in block size and other details may not be entirely compatible unless you're using two exactly identical drives.

You might want to create another partition of the same type and size, create the same filesystem and do a **sudo cp -rax /mnt/original /mnt/duplicate** on it.

If you're bent on using dd, then it would be approximately **sudo dd if=/dev/sda3 of=/dev/sdb3 bs=4194304**. Adjust if and of for correct drive and partition. bs is block size, the number of bytes transferred at a time. If you leave it to the defaults it will take forever. Note that bs needs to fit in memory and is best if it matches a multiple of the block size on your drive.

---

### Post by QDR06VV9 on 2016-04-28
[COLOR=#ff0000]*****WARNING***PLEASE REFER TO oldfreds post below before following this post**[/COLOR]
I boot to a live usb installer for Xenial then went to the Menu>System Tools> Mate Terminal...click that.
In the Terminal I issued this command
```
sudo fdisk -l
```
Which gave me the needed info for the next step.
The fdisk -l shows me this
```
________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008e5ea

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 554589938 554587891 264.5G 83 Linux
/dev/sda2       964194302 976769023  12574722     6G  5 Extended
/dev/sda3       554592256 964191865 409599610 195.3G 83 Linux
/dev/sda5       964194304 976769023  12574720     6G 82 Linux swap / Solaris

Partition table entries are not in disk order.

Disk /dev/sdb: 465.8 GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf1a41731

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048    524287    522240   255M 83 Linux
/dev/sdb2          524288 964536319 964012032 459.7G 83 Linux
/dev/sdb3       964536320 976771054  12234735   5.9G  f W95 Ext'd (LBA)
/dev/sdb5       964538368 976771054  12232687   5.9G 82 Linux swap / Solaris
___________________________________________________________________



```
Where sda is the source I want to clone. **This may be different for you**
Now sdb will be the target or where i want the cloned Partitions to go. **This may be different for you**
So in the Terminal I next issued
```
sudo dd if=/dev/sda of=dev/sdb
``` [B]Again sda and sdb may be different for you
[/B]Now just set back and watch the magic and when done boot to your newly cloned partition.

---

### Post by Old Jimma on 2016-04-28
Hi 1clue:

I think what you have described is exactly what I want to do. How do I create a partation with the same block size on the output file (of)? Should I use gparted? It is a 3Tb drive.

(I'm using photorec to recover lost jpgs, and want to make sure that partition has exactly the same characteristics as thd input file (if).

THanks,
Old Old jimma

---

### Post by oldfred on 2016-04-28
DO NOT use dd on gpt partitions. It can be used on an entire drive, but partition table & backup partition table have unique GUIDs that must match partition. If you copy a partition then you need major repairs which may be possible with sgdisk.

If using photorec just have it restore found files to partition on new drive.

---

### Post by jerome1232 on 2016-04-28
If this is just a data partition. Honestly I'd just use a good 'ole rsync to copy the data from partition to partition. No reason to do a byte for byte copy.

---

### Post by Old Jimma on 2016-04-28
> **him610 said:**
> You might consider using clonezilla instead of dd.
You can read about it here....
[http://clonezilla.org/]("http://clonezilla.org/")

I can't use rsync.... I need dd because I"m trying to recover lost files that have "lost directories."

---

### Post by 1clue on 2016-04-28
OK you're leaving out critical information.

First, how big is the original partition? Why would using dd help you recover the files?

I've never had much luck recovering lost files. I'm not sure if dd is your friend here either. I didn't think of the gpt partition table needing correct guid's like oldfred said. That is true, and it means dd WILL NOT WORK on gpt partition tables.

What might work is to make a larger-than-the-original partition on the new drive, then use dd to copy the original partition over as though it were a regular file. It could then be mounted as a loopback partition probably. Not knowing much about file recovery I'm not  likely to offer useful information about it.

---

### Post by Old Jimma on 2016-04-29
HI 1clue:

Thanks for your reply.

On many occasions, I've copied paritions that I already know are the same size (or output file for dd is larger) with dd, and then use photorec to find lost files. I've done this many time for myself and friends who lose important files. photorec works well. Try it. You'll like it.

This means dd will work on "gpt" parition tables.

I sure wish somebody would just answer my question

> How do I create a partition of a specified size.

Thanks,
Old JImma

---

### Post by sudodus on 2016-04-29
I suggest that you use ***gparted***. It has an easy graphical user interface and lets you select size in Mibibyte units (2^20) bytes.

If you prefer a command line tool you can use ***parted*** (and use a separate tool to create the file system). Then you can select size more accurately, but you should be careful to match the start of a partition with the sectors of the drive.

Both tools work with MSDOS and GUID partition tables (GPT).

---

### Post by 1clue on 2016-04-29
What dd will not do is copy a partition from one gpt drive over the top of the partition for another gpt drive. Each drive will have a unique UUID, and if the UUID is wrong then the partition table is corrupt.  The UUID will NOT be the same between the two drives.

So your best bet is to create a (probably 20%) larger partition on the second drive, format it and then dd the first drive's partition over to a file on the second drive.

You can then use photorec on that file. If photorec needs the partition to be mounted you can mount it using -o loopback

---

