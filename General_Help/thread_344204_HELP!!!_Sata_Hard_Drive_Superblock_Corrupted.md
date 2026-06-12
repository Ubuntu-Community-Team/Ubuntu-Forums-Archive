---
title: "HELP!!! Sata Hard Drive: Superblock Corrupted"
date: 2007-01-22
forum: General Help
---

### Post by jofre on 2007-01-22
Ok, that's what happend: I was watching a movie I have in my sata hard drive (not where Ubuntu Dapper is installed), and suddenly the computer froze. I restarted the computer and I get a message saying that the /dev/sda2 superblock is corrupted!

I try to use google but without luck.
I come acros with e2fsck and TestDisk, but they don't seem to see my sata hardrive!

The Disks utiliy is the only application that can see it, but not mount. Gparted can't see it.

Please, any ideas? 
I have a lot of pictures there! The bloody hard drive is less than 6 month old!!!

Please HELP!!!

---

### Post by jofre on 2007-01-22
Nobody has any idea?

---

### Post by jofre on 2007-01-23
Well just posting again as I would really appreciate some help recovering the dat on the Hard Drive:roll:

---

### Post by bodhi.zazen on 2007-01-23
Check out testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by jofre on 2007-01-23
Thanks Zazhen, 

I had already tried TestDisk, but it does not see the hard drive. Funny enough I get this:

tango@tango-desktop:~$ testdisk /list
TestDisk 6.1, Data Recovery Utility, October 2005
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/hdc - 4184 MB - CHS 134 255 63, sector size=2048

Disk /dev/hdc - 4184 MB - CHS 134 255 63
     Partition                  Start        End    Size in sectors
Partition sector doesn't have the endmark 0xAA55
TestDisk exited normally.

When, in theory, I don't have any device called hdc! or at least, I use to have:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/windows  vfat  iocharset=utf8,umask=000  0    0

# New Hitachi-250GB hard drive. I put two partitions: 25GB FAT32, and the rest with Ext3
/dev/sda1    	/media/HitachiFAT32  vfat  iocharset=utf8,umask=000  0    0
/dev/sda2       /media/HitachiExt3   ext3    defaults,errors=remount-ro 0       1

I had disconnect hdb1 because I thought it may be faulty, and now, after the freeze I was talking about, I can't mount neither hdb neither sda!!! Lucky enough that hda (where Ubunut lives) is still ok!!!

Thanks anyway for the help.
If you have any other ideas... I have been looking to google for hours ](*,)

---

### Post by jofre on 2007-01-24
Just in case this helps:

The message I get at start up (when it trys to mount the devices listed in fstab) is:

* Checking all filesystems...
fsck.ext3: Nosuch file or directory while trying to open /dev/sd2
/dev/sda2:
The superblock could not be read or does not describe a correct ext2 filesystem. If the devices is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>



When get to my system, I type the suggesed and I get:

tango@tango-desktop:~$ e2fsck -b 8193 /dev/sda2
e2fsck 1.38 (30-Jun-2005)
e2fsck: No such file or directory while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

tango@tango-desktop:~$


Any ideas/suggestions (apart from buying a new hard drive!)?

---

### Post by jofre on 2007-01-27
Came on lads? 

Nobody has any idea? I have tried everything I know!!!

---

### Post by jofre on 2007-01-29
Well, well, well. I found the problem!!!:D :D :D 

I had bought a power splitter cable some months ago, and look like it is now faulty, so the hard drive was not powered at all!!!!!](*,) ](*,) ](*,) 

So there you go. Problem solved, I am up and running again!

---

