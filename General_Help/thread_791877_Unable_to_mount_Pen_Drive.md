---
title: "Unable to mount Pen Drive"
date: 2008-05-12
forum: General Help
---

### Post by Shiv Prakash on 2008-05-12
Hey,

I am unable to mount my usb pen drive
this is what i get for fdisk -l

```
:~$ sudo fdisk -l
```

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fd11fd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       29185   213455655    f  W95 Ext'd (LBA)
/dev/sda3           29186       30401     9767520   83  Linux
/dev/sda5            2612       27691   201455068+   7  HPFS/NTFS
/dev/sda6           27692       28907     9767488+   b  W95 FAT32
/dev/sda7           28908       29185     2233003+  82  Linux swap / Solaris

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
 

I created /media/disk1 and tried this

```
:~$ sudo mount /dev/sdb /media/disk1
```
> mount: block device /dev/sdb is write-protected, mounting read-only
mount: you must specify the filesystem type

Can someone please help
Thanks

---

### Post by tenuki on 2008-05-12
Hey shiv,

So it looks like the stick is completely unformated. To load it you'll need to create a partition table (even if it's only 1 partition across the whole disk) and make a filesystem by formating the device.

Use fdisk to create partition table:

```
fdisk /dev/sdb
```

In fdisk use "n" command to create a new partition, and don't forget to use "w" to write the new partition table before exiting.

Now you can put on the filesystem:

```
mkfs.vfat /dev/sdb1
```

(Note that device is /dev/sdb, but you format/mount the partition /dev/sdb1)

That's it. Should be able to mount using "mount" command, or unplug and stick back in to see if Ubuntu detects automatically.

Hope that helps.

---

### Post by tenuki on 2008-05-12
Sorry, might need to prefix those commands with "sudo". Doh!

---

### Post by Shiv Prakash on 2008-05-12
This is what i did

```
:~$ sudo fdisk /dev/sdb
```
> You will not be able to write the partition table.
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6798119a.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1015, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-1015, default 1015): 1015

Command (m for help): w

Unable to write /dev/sdb


??????

---

### Post by chrisccoulson on 2008-05-12
> mount: block device /dev/sdb is write-protected, mounting read-only
Is there a write-protect switch on the side of the pen drive?

---

### Post by Shiv Prakash on 2008-05-13
> **chrisccoulson said:**
> Is there a write-protect switch on the side of the pen drive?

I checked...no there isn't any write protect switch on the pen drive....

---

### Post by Shiv Prakash on 2008-05-13
bump...

---

### Post by tenuki on 2008-05-13
I can see that I'm rapidly reaching the limit of my knowledge. If we can't write the partition table, then I'm guessing that there's something hardware-related that we're missing. Especially with the write-protection warning.

Is this the first time this USB stick has ever been used? If you have access to a Windows/Mac, what happens when you plug it in there?

---

### Post by DrCoolSanta on 2008-05-13
Is this a new pen drive? If its not, then try to open it in windows or mac (like the above guy said) and try to format it (ie if it doesn't work), if it is then also check if it works normal on other OSs, and if not, make use of its warrenty.

It might be possible that it has two partitions for protection, a pendrive of mine was like that, unfortuantelyI couldn't do anything, its partition table was protected. But then I was able to mount it.

---

### Post by tenuki on 2008-05-13
It might be worth seeing if you get any joy using parted/gparted for writing the partition table instead of fdisk. However, if the stick used to work and has now stopped, then to me it sounds like it might be dead.

---

