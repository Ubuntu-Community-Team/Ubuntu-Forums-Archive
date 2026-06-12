---
title: "Can't access old internal hardrive"
date: 2018-05-02
forum: General Help
---

### Post by zuto2 on 2018-05-02
Okay, I am trying to access an old harddrive that was in my old computer that no longer works. I dual booted Ubuntu 12.04 with Windows 7 on a 32 bit system. I had no luck accessing the harddrive with Windows 10.


I am currently using a 64 bit computer and I am trying to access my data using an adapter called Kingwin ADP-10. It allows me to access the hardrive with a usb port.


I want to access the harddrive because I did not get to back up my opensource video game project that day on Ubuntu. I did a lot of work in those 24 hours and it would be a total waste if I cannot save it.


I tried a few things before making this post.


**Disks:**


As you can see, the filesystem is raw device (sdb)
[IMG]https://s9.postimg.cc/v8bx797b3/Selection_001.png[/IMG]


[B]Gparted:
[/B][IMG]https://s9.postimg.cc/q9oespvsf/GParted_002.png[/IMG]




```
sudo mount /dev/sdb /mnt/
mount: /dev/sdb: can't read superblock


sudo mount /dev/sdb6 /mnt
mount: special device /dev/sdb6 does not exist



```

And a quite a bit of other things:
[https://paste.ubuntu.com/p/f39y2BHXnG/](https://paste.ubuntu.com/p/f39y2BHXnG/)

---

### Post by yancek on 2018-05-02
Do you have any partitions with filesystems on that drive and if so, what filesystem is it.  Mounting the drive (/dev/sdb) usually won't work although it is possible if you have a filesystem on it.  Did you run fdisk or parted to see what partitions you have on the drive and the type of filesystem.

---

### Post by zuto2 on 2018-05-03
> **yancek said:**
> Do you have any partitions with filesystems on that drive and if so, what filesystem is it.  Mounting the drive (/dev/sdb) usually won't work although it is possible if you have a filesystem on it.  Did you run fdisk or parted to see what partitions you have on the drive and the type of filesystem.

I have a window 7 and ubuntu 12.04 partitions. I am pretty sure I am used NTFS for Windows and ext3 for Ubuntu 12.04.

I used  fdisk as I stated in the [paste]("https://paste.ubuntu.com/p/f39y2BHXnG/"):

```
 [COLOR=#000000]sudo fdisk -l[/COLOR]
```

Although, it said nothing on (/dev/sdb). I could have used it incorrectly because I am not familiar with the commands. I might have damaged sectors, but no clue on how to fix something I can't mount. 

When I used:

```
dmesg
```

It said something about the following and a load of other stuff:

```
Buffer I/O error on dev sdb, logical block 0


critical target error, dev sdb, sector 488396928
```

---

### Post by hrsetrdr on 2018-05-03
Maybe you could format your Kingwin ADP-10 and put a file system on it.    Then you can copy your files from the old internal drive.

---

### Post by zuto2 on 2018-05-03
[COLOR=#101010][FONT=&quot]> [/FONT][/COLOR][COLOR=#000000]Maybe you could format your Kingwin ADP-10 and put a file system on it. Then you can copy your files from the old internal drive.[/COLOR][COLOR=#101010][FONT=&quot]

Doesn't formatting a hard drive mean to delete any information on the drive?[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-05-03
Sorry to hear this, but have you considered using testdisk: [https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

It might not restore your partion but there is a good "chance" you might be able to recover some or all of your data. 
Best of Luck though.

---

### Post by dino99 on 2018-05-03
First go to the bios to know if the hdd is found; then start gparted to see if a 'red triangle' or other symbol identify and error about that disk or partition (could need to rebuilt the partition(s) table: cant damage the data).  If nothing catch your attention, then run fsck (linux) or defrag (windoz)

---

### Post by yancek on 2018-05-03
No need to format and with Linux you should NOT mount a partition to run a filesystem check with fsck on that partition.  Do you get no results running?  I see references to sdb in your initial post paste link but best to check the BIOS because if it isn't seen there, it won't be seen from Linux or windows.

> sudo fdisk -l /dev/sdb

---

### Post by zuto2 on 2018-05-03
```
sudo fdisk -l /dev/sdb


fdisk: cannot open /dev/sdb: Input/output error

```

Testdisk could not detect the partitions. I think the only thing I can do is reformat it. In any case, if the partitions are damaged, then my old laptop is not broken. I lost power when at the grub partition menu and that might have messed things up. If no one has anymore ideas, then I can at least see what else I can do with this hardrive.

I am always very grateful for the Ubuntu community for at least trying to assist me.

---

### Post by yancek on 2018-05-03
You didn't indicate whether the drive was seen from the BIOS?  Last idea I have.

---

### Post by #&amp;thj^% on 2018-05-03
One last thought for me as well, I have seen some adapters like the one you are using now not read disks properly>>>Have you at least tried hooking it in your computer as a second Hard Drive? (If Possible)
I like having many attached to mine so I can religiously back up every night. (Don't take that in a Ill manner,  just what I have learned though out the years the hard way)

---

### Post by zuto2 on 2018-05-05
Heh, I have a few of the same hard drive and the adapter works on them all without a problem. I believe it is damaged due to a power surge that killed my old laptop. It won't even let me reformat it and it is not seen by the BIOS.

I am grateful for the assistance. I at least learned a few new tricks. I may not be able to recover the boss sprite, but I can easily rewrite the code that was lost.

---

