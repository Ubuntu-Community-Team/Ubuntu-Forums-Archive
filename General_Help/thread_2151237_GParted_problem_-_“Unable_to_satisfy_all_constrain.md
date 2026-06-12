---
title: "GParted problem - “Unable to satisfy all constraints on the partition”"
date: 2013-06-03
forum: General Help
---

### Post by KonyKing on 2013-06-03
[COLOR=#333333][FONT=Ubuntu Beta]I have a dual-boot system and I wanted to shrink the Windows partition to give more space for Ubuntu. So using GParted, I was able to properly shrink the Windows partition, leaving some unallocated space to be used by the Ubuntu partition. Then when I was trying to extend the Ubuntu partition to include the unallocated space, I get an error from GParted that says "unable to satisfy all constraints on the partition". I have tried basically everything, but I just can't make this error message go away. Any help would be much appreciated! :)


[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]KonyKing; 

From advise I have seen;
One should have used Windows' tools. First to defrag Windows's at least twice and  to resize the Windows' partition, then run Windows' check disk utility twice to obtain the "unallocated space in which to install ubuntu onto, such that there are no complaints.

edit: I failed to Welcome you to the forum, I wish the best to you.

Hate to be the harbinger of ill news, but, I suggest a Windows' repair CD.
[/COLOR][INDENT=2][COLOR=#000000]
windows tools for Windows' problems and linux tools for ubuntu situations
 [/COLOR][/INDENT]

---

### Post by KonyKing on 2013-06-03
I don't think you understood my question. I have successfully shrunk my Windows partition and I can still boot into it properly. Now the problem lies in resizing the ubuntu partition to include the unallocated space. I just keep getting that annoying error message.

---

### Post by ahallubuntu on 2013-06-03
~

---

### Post by fantab on 2013-06-03
Post the output of:
```
sudo fdisk -l
```
and 
```
sudo parted -l
```

---

### Post by VMC on 2013-06-03
Have you rebooted since you adjusted the Windows partition? If your afraid you'll lose your Ubuntu, then on a terminal type the following so we can see if any errors show up.

```
sudo sfdisk -l
```

edit-I  see someone beat me to the fs listing.

---

### Post by KonyKing on 2013-06-03
I am using Ubuntu 13.04 and GParted 0.12.1. I don't think the problem is with my partition table.

here is a screenshot:

[IMG]http://i.imgur.com/23U8yFX.png[/IMG]

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]KonyKing;

I might have an inkling of what is going on. Are you trying to extend the sda5 partition ? Prior to extending the "container" of that partition sda4 ?

Else, the afore mentioned terminal commands will provide us additional information.
[/COLOR][INDENT][COLOR=#000000]
where there is a will there is a way 

[/COLOR][/INDENT]

---

### Post by KonyKing on 2013-06-03
here you go:
```

yonathan@yonathan-Satellite-M645:~$ sudo fdisk -l
[sudo] password for yonathan: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9d9d95d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048   801099775   399012864    7  HPFS/NTFS/exFAT
/dev/sda3       954488832   976773119    11142144   17  Hidden HPFS/NTFS
/dev/sda4       914061310   954488831    20213761    5  Extended
/dev/sda5       914061312   946522111    16230400   83  Linux
/dev/sda6       946524160   954488831     3982336   82  Linux swap / Solaris


Partition table entries are not in disk order
yonathan@yonathan-Satellite-M645:~$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs            boot, diag
 2      1574MB  410GB   409GB   primary   ntfs
 4      468GB   489GB   20.7GB  extended
 5      468GB   485GB   16.6GB  logical   ext4
 6      485GB   489GB   4078MB  logical   linux-swap(v1)
 3      489GB   500GB   11.4GB  primary   ntfs            hidden




yonathan@yonathan-Satellite-M645:~$ 

```

---

### Post by fantab on 2013-06-03
This could be tricky as I have not done this before. BACK UP your DATA first.

Firstly, the 'unallocated space has to be added to the Extended Partition, /dev/sda4, then to the /dev/sda5 and then you have /dev/sda3 between unallocated space and /dev/sda4.

---

### Post by VMC on 2013-06-03
I'm unsure if you can merge that unallocated with the logical. You might be able to add it to the extended partition then merge it.

A better way is this. Use partclone, then delete the extended and swap and start over and include the unallocated. Then create a swap and a new Ext4 partition of the size you want. Then use the image you created with partclone to restore the image you created to the new partition. Sounds more complicated than it really is. You would need to tell the new ubuntu partition where the new swap is (UUID wise).

Install partclone:
```
$ sudo apt-get install partclone
```
Image Ubuntu
```
$ sudo su
# partclone.ext4 -c -s /dev/sdaX|gzip -c --fast>ubuntu.gz
```

Restore
```
# zcat *image.gz*|partclone.ext4 -r -o /dev/sdaX
```

After restoring to a newer larger partition you need to either use gparted to resize or use the command yourself:
```
$ man resize2fs
```

---

### Post by KonyKing on 2013-06-03
I don't quite understand what you're proposing here.

---

### Post by VMC on 2013-06-04
> **KonyKing said:**
> I don't quite understand what you're proposing here.

This is what I'm proposing:
[IMG]http://i.imgur.com/kkgVXOk.png[/IMG]

---

