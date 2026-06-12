---
title: "DD_Rescue help"
date: 2006-12-13
forum: General Help
---

### Post by shawnanigans on 2006-12-13
I cant get dd_rescue to write an image of my broken *** hard drive. This is what I have gotten.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14947   120059856    b  W95 FAT32
ubuntu@ubuntu:~$ dd_rescue /dev/sdb1 /dev/sdc1/disk.img
dd_rescue: (fatal): open "/dev/sdb1" failed: Permission denied
ubuntu@ubuntu:~$ sudo dd_rescue /dev/sdb1 /dev/sdc1/disk.img
dd_rescue: (fatal): open "/dev/sdc1/disk.img" failed: Not a directory
ubuntu@ubuntu:~$ sudo dd_rescue /dev/sdb1 /dev/sdc1/"disk.img"
dd_rescue: (fatal): open "/dev/sdc1/disk.img" failed: Not a directory
ubuntu@ubuntu:~$ 

Also i am a complete newb and i am running of the edgy eft live cd.

---

### Post by maniacmusician on 2006-12-13
I have to learn how to use this program as well, so I'm interested in the responses.

---

### Post by cilynx on 2006-12-13
It's looking for a directory to dump the disk image into.  You're giving it a full path to the image.  Lop off the disk.img and see what you get.

---

### Post by shawnanigans on 2006-12-13
i did that previously and it didn't write an image it wrote a bunch of nonsense files. It was a copy of a 120gb drive and there was only about 300mb of files and none of those were readable.

---

### Post by maniacmusician on 2006-12-13
yes, I tried data recovery with photorec and I got things like that too. Except I got the right amount, much more than what you're getting. I think the integral questions is:

Is there any data recovery tool that can effectively recover files **while retaining their file and folder structure?** This includes preserving correct filenames, etc.

---

### Post by cilynx on 2006-12-13
That's generally what you get with data recovery from tanked hardware.  There's a reason "computer forensics" experts make the big bucks.  

As for the health of the thread, I too am very interested in people experiences with data recovery.  I've had similar situations with many different packages.  Autopsy / Sleuthkit is my current tool of choice.

---

### Post by shawnanigans on 2006-12-13
the thing is the disk shouldnt be terribly damaged, i was trying to change the partition size in Partion Magic and it stopped booting. I assume most of the stuff should be alright. And really I only want a few files. I might have a bad superblock so most of the data itself should be alright or so what little knowledge i have tells me.

---

### Post by miclo987 on 2007-01-03
Hello,

Please due the following at your own risk because dd, dd_rescue are very dangerous commands try to do it on a system you don't care about.  I have never done a whole drive with dd_rescue but with floppies and cds due to not having enough disk space on my dual boot system.  I have done it at school with dd and it usually works have you tried that? this dd_rescue seems buggy the helix cd usually works fine ([http://www.e-fense.com/helix)](http://www.e-fense.com/helix)). I keep getting errors but my floppy and cd drive are old.  The latest version is at [http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/) but only gives instructions on compiling in redhat.  I don't know how to compile in ubuntu. The newest version is 1.12 ubuntu version is 1.10.

dd_rescue example:
1. sudo su
2.  mount filesystem (e.g. mount -t ntfs /dev/hda1 /mnt hda1) dont forget to make a directroy in /mnt for the filesystem
3.  make a directory somewhere (e.g. mkdir temp1)
3.  go to that directory (e.g. cd temp1)
4.  dd_rescue /dev/sdb disk.img or .bin or .dd
5.  if you run into errors try the -r command 

if you have another hard drive and want to totally overwrite it first format then
try
replacing dd_rescue /dev/your drive /dev/another drive  (this will delete the other drives contents)

dd and dd_rescue do byte by byte copys so you will get the exact data copied

note:  I keep running into input/output error with ubuntu dd_rescue version but im only trying floppies and cds because of space so hopefull it will work for you.  you may just want to try dd.
every time I mount in losetup as a loopback it doesn't find a valid partition table.  I forgot how to set up a loopback with the mount command so i haven't tried that.  if worst comes to worst maybe some of the ftk tools can help (fls -d /dev/sdb)

well i hope this helps get you started

sincerely,
miclo

---

### Post by miclo987 on 2007-01-03
opps sorry

at /dev/sdb put what ever device your trying to copy

---

### Post by robenroute on 2007-01-03
There's actually a very good short write-up on recovering data from (damaged) disks on [this]("http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html") page.

Hope this is helpful....

---

