---
title: "Help formatting an external Macintosh hard drive..."
date: 2013-07-10
forum: General Help
---

### Post by Nixarter on 2013-07-10
I got an external hard drive made for macintosh computers on clearance for really cheap (because it is for mac's, and nobody owns macs! lmao lucky me).  I dont want it in the macintosh format, though.  I want it in NTFS for my usage.

1.  Ubuntu reads the drive fine, but I cannot tell what format the drive is in.  I'm guessing in some kind of macintosh format, because the box says i must refromat for use with windows PC's (in other words, it isn't in NTFS).  But, when I hit properties i cannot find the drive format type.  How can I do this?

2.  How do i format it from within ubuntu? (12.04)  Everything I can find says go to a boot disc or something, and i can't how to figure out how to bring up the list of drives showing "sda1" and so forth that I keep seeig mentioned.  And, jsut as importantly, I don't know how to tell which drive is SDA, SDB, and so on from the txt.

The drive is new and basically empty.  just some original mac programs that came with the drive.  so I dont need to save anything.  i just want a fresh new NTFS drive.

---

### Post by Nixarter on 2013-07-10
ok, i found the command...

```
sudo fdisk -l
```

it lists sde as having no valid partition table.  Does that mean it is the mac one?  Ubuntu reads it fine, which is weird.

edit: i have two 2tb drives hooked up atm.  one with 
no valid partition table" shows a disk identifier as 0x00000000 (and so on),. as does another drive (not a 2tb).  Is that significant?  And also, that drive is 512b/sector, and the other ne is 4096.  Which one is likely the MAC one?

---

### Post by Nixarter on 2013-07-10
OK, I managed to find a vid on youtube...


[ubuntuhal - How to format a drive to NTFS using Gparted]("https://www.youtube.com/watch?v=LApK79kc4jE")

Luckily. Gparted had the drive name My Book, which is the type of drive the Macintosh drive is, so it was much easier to identify than guessing which SD* it was.

I managed to delete 2 partitions and reformat to NTFS.  I still had an error and one partition would not delete, and there is still "no valid partition table."  But, the drive seems to work fine.  I'm going to test it in windows, and as long as it works, I'll leave it as is.

So, as for now, I will mark it as solved.  but I will check back as I would still like to know why there was an error deleting the 32kb or whatever partition.  It said it saved a file with data that would help troubleshooting to my desktop, but it lied.  there is nothing there.

edit: well, apparently they removed the solved thread option from thread tools.  meh.

---

### Post by SBJ95 on 2013-07-10
Curious, what happens if you open it in fdisk (sudo fdisk /dev/sd**x**), then do an **o** to create a new partition table?  Then you can use a tool of choice (I know I like fdisk) to create a partition, and set it to type 87 for NTFS.

You need to ensure you have ntfsprogs installed (sudo apt-get install ntfsprogs), then you can do a 'mkntfs /dev/sd**x**'.  

Let me know if this fixes that last little problem.

---

### Post by Nixarter on 2013-07-10
```
admin@ubuntu:~$ sudo fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x0f2g4721.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
admin@ubuntu:~$ partprobe
admin@ubuntu:~$ sudo fdisk /dev/sdc

Command (m for help):
```

then I opened up the disk in Gparted again and it came up 100% unallocated (so yes, that problem is fixed :) )

Then I had to unmount the drive, physically unplug it, then plug it back in.  Then reopened gparted, which listed it as sdd instead of sdc as it wasa before.  Then I created a partition table from there, added a new NTFS partition and now it uses 100% space (from 99.999% or so) and has a partition table.  :)  Thanks a lot

---

### Post by SBJ95 on 2013-07-10
Glad I could be some help!

---

