---
title: "screwed NTFS partition inside an extended one"
date: 2007-12-31
forum: General Help
---

### Post by anthonie on 2007-12-31
Hi,

I somehow managed to loose my NTFS headers on a partition located on my second harddrive. How it happened, I don't know, but the partition not only lost it's headers and is therefor unallocated, now it also resides inside an extended partition that did not used to be there before. 

I tried testdisk on other occasions, with succes, but not so much luck this time as it does not recognize the ntfs, actually the whole unallocated space is not being seen. Gparted on the other hand shows me the partition, as being part of the extended partition. 

How would I go about and get this thing fixed? What info do you need to be able to point me somewhere?

---

### Post by taurus on 2007-12-31
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```
Is there any data on that harddrive?

---

### Post by anthonie on 2007-12-31
The outcome of sudo fdisk -l is as follows

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c641c63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2472    19856308+   7  HPFS/NTFS
/dev/sda2            2473        3792    10602900   83  Linux
/dev/sda3            4712        4865     1237005    5  Extended
/dev/sda5            4760        4865      851413+  82  Linux swap / Solaris
/dev/sda6            4712        4759      385497   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbd94990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       36266   291298612+   f  W95 Ext'd (LBA)
/dev/sdb5           29621       36266    53383963+   7  HPFS/NTFS

On the second harddrive there is a Vista partition (sdb5) and within the extended there is a lot of unallocated space that used to be a NTFS partition, full of my favorite songs and movies and all that sort of personal stuff, ... Nope, no backup.

---

### Post by taurus on 2007-12-31
Did you you remove XP on /dev/sdb and play around with the partition table?

---

### Post by anthonie on 2007-12-31
> **taurus said:**
> Did you you remove XP on /dev/sdb and play around with the partition table?

No, it was a storage space in NTFS for a good couple of years. Over the years the the drive had become a real mess. So when I recently wanted to try and install Gentoo, I figured a clean up was needed first. I removed a couple of partitions, and somehow I must have been not carefull enough and ended up with the mess above. Note, for instance, that I also have (AFAIK) an unnecesary second SWAP space on my first harddrive. 

So, as far as I can plan at the moment this is more or less what I would like to do:

Get the NTFS header REwritten to the partition inside the extended one on the second harddrive (currently Gparted tells me it's unallocated space). If that succeeds, clean up all partitions that are not needed.

---

### Post by cdenley on 2007-12-31
If it lost the ntfs headers, what makes you think your files are still there? Maybe you can try creating a new ntfs partition of the same size, then copy the headers from the empty partition. I'm not sure that will work, just an idea.

Whatever you try, you should backup the partition first, in case you mess it up.
```

sudo cat /dev/sdb5>broken.img

```

---

### Post by anthonie on 2007-12-31
> **cdenley said:**
> If it lost the ntfs headers, what makes you think your files are still there? [quote]
Because Photorec, prog that comes along with the testdisk program actually is able to find them. Within the Extende LBA partition. However, its estimations on recovery time go beyond my wildest dreams. It already estimated 72 hours and was not even finished indexing what is there.

Also, the files it recovers loose their filenames, which is kind of nasty. The thing is, I never formatted the partition that is lost. I tried to create some another for a Gentoo install. So, I thought I might still have some data left. So that is how testdisk came into the picture, and with it, Photorec.

[quote]Whatever you try, you should backup the partition first, in case you mess it up.
```

sudo cat /dev/sdb5>broken.img

```

I would love to, but unfortunately I have no space for that.

---

