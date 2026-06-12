---
title: "Missing  Lots of Hard Disk space"
date: 2012-11-17
forum: General Help
---

### Post by feesthoed on 2012-11-17
At first I'd like to excuse me for my semi-broken English. 
Anyhow, here we go ! [IMG]http://www.linuxhelp.net/forums/style_emoticons/default/smile.gif[/IMG] 

So I'm experiencing this problem, the problem where my HDD only shows 30MB out of the 1TB. 
The thing is, before this problem acquired I had some other problems with my system thanks due GRUB. 

Let me give you guys an idea what was going on.
I have 3 disks, 
- A 64GB SSD which contains my Windows 8 installation 
- A 1TB HDD which held my Windows 8 files and programs
- A 160GB HDD which had Back Track 5 upon it 


Two nights ago I partitioned my 160GB  disk which had a copy of Back Track 5 upon it. 
Everything went smooth and so until the next morning when I tried checking my email.
Upon boot I received a GRUB message error stating '' Grub can't find such device'' 
Silly  me with my enormous silly head feared all of my disks being corrupt and  before I knew I unplugged my 1TB HDD which held all of my personal  files and took it with me to school. (of course after turning the  computer down) Once there I directly plugged my disk into my personal  school computer (Windows XP) hoping to see any living file. Sadly enough  things didn't went that smooth enough. 
I did saw my hard drive, but  once I clicked upon it I was prompted with a error message box which  said that my hard disk needed a reformation. After consulting  Diskmanagement and USB-HDD connected I finally asked my teacher for some  aid. He then tried connecting the hard disk to his computer (Fedora)  but once again it was a no no. Later that day I found out why my Grub  Loader was somewhat bugged and once home I used this guide 

- howopensource.com/2011/08/restore-mbr-from-ubuntu-live-cd-usb/

It  went smooth and I was able to boot my Windows Installation. There I  finally could see my HDD without the need of a reformation, the only  minor was the drive being 30MB out of the 1TB. 
Without to much  thinking I reformatted the drive because I was planning to use File  Recovery Software anyhow. Windows 8 Diskmanagement is also not able to  detect the whole TB, just like the Ubuntu Live USB when in Installation.  

Thus leaving me here, clueless what to do. I do have a theory tho. 
Would it be due my teacher putting the drive into his Fedora system ? 
Anyhow. I'm looking forward to any response. Feel free to ask me anything ! 

Yannick.
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3562bf50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   117227519    58510336    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5979

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312579759   156289848+  42  SFS

Disk /dev/sdc: 33 MB, 33348608 bytes
180 heads, 48 sectors/track, 7 cylinders, total 65134 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             128       59519       29696    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 3868 MB, 3868430336 bytes
255 heads, 63 sectors/track, 470 cylinders, total 7555528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *         128     7555455     3777664    b  W95 FAT32


---

### Post by dino99 on 2012-11-17
isn't all the difference between bits & bytes ?

[http://www.beesky.com/newsite/bit_byte.htm](http://www.beesky.com/newsite/bit_byte.htm)
[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

---

### Post by feesthoed on 2012-11-17
> **dino99 said:**
> isn't all the difference between bits & bytes ?

[http://www.beesky.com/newsite/bit_byte.htm](http://www.beesky.com/newsite/bit_byte.htm)
[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

Excuse me, but I can't really follow. 
Any chance you could explain it a bit ?

---

### Post by Mark Phelps on 2012-11-17
Sorry, but a partitioning utility telling you your (former) 1TB drive is now ONLY 30GB is anything BUT a minor problem.

If you really want to get the contents of that drive back, you need to strongly consider using MS Windows utilities -- as my experience has been that Windows utilities to a better job of data recovery on Windows filesystems and Linux utilities do a better job of data recovery on Linux filesystems.

You will need to be able to remove the (former) 1TB drive and connect it to a Windows PC -- to do the file recovery.

If you're interested in doing that, the look into then downloading and installing RecoverMyFiles (from Runtime Software) on the Windows PC, scanning your drive in the deepest recovery mode, and then seeing what it finds.  IF it finds what you want to recover, you will have to go online and purchase a license for the product.

Your data -- your money -- your choice.

---

### Post by feesthoed on 2012-11-17
> **Mark Phelps said:**
> Sorry, but a partitioning utility telling you your (former) 1TB drive is now ONLY 30GB is anything BUT a minor problem.

If you really want to get the contents of that drive back, you need to strongly consider using MS Windows utilities -- as my experience has been that Windows utilities to a better job of data recovery on Windows filesystems and Linux utilities do a better job of data recovery on Linux filesystems.

You will need to be able to remove the (former) 1TB drive and connect it to a Windows PC -- to do the file recovery.

If you're interested in doing that, the look into then downloading and installing RecoverMyFiles (from Runtime Software) on the Windows PC, scanning your drive in the deepest recovery mode, and then seeing what it finds.  IF it finds what you want to recover, you will have to go online and purchase a license for the product.

Your data -- your money -- your choice.

Actually it only detects 30MB, and I do already have a file recovery program (a friend who owns it) called Stellar Phoenix. Scanned with their deepest rec. method and found literally nothing  expect some trash files.

---

### Post by feesthoed on 2012-11-17
Really no one who knows what to do ?

---

