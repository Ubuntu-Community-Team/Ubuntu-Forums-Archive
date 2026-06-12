---
title: "making [mounting?] /swap"
date: 2008-02-14
forum: General Help
---

### Post by the badger on 2008-02-14
(i'm just learning about all this 'puter stuff, so please bear with me...)

i realised i have no swap partition. i re-installed when gutsy came out, wound up with a grub error, and created a /boot partition. can't remember the whole process, so now i'm wondering if i should've made a swap partition and didn't.

i think this might be important because since installing gutsy my system has been really slow. and swap is virtual memory, right? [i've got an older system with 512MB ram. ubuntu only - no dual boot].

can someone instruct me on creating a swap partition (or let me know i don't need it)? i can copy and paste, but i'm a simpleton with the command line [noob].
   i have:
   dev/hdb3 -> /
   dev-hdb1 ->/boot
   and a ghostlike nfsd partition (nothing allocated, nothing used).

graciously thanks.

---

### Post by Gen2ly on 2008-02-14
gosh, I think the best bet would be just to create a swap file.  You can move and resize your partitions if you like with gparted on the livecd but its not really... well its more than what required.  Oh, and swap isn't virtual   memory, its memory thats paged from the hardware memory (RAM) to the disk when RAM gets used up.   512 is ok for most system, add the system monitor applet to the panel (if it isn't already and take a look and see what your memory usage is.  If you find you need it, creating a swap file is easy:

first create the file.
```
dd if=/dev/zero of=/swap bs=1024 count=2097152
```

&#8226; Swap is recommended to be 1-1/2 to 2x the value of the RAM to use for hibernation.
&#8226; 1 GB = 1024 MB = 1024 x 1024 kB = 1048576 kB = 1048576 kB x 1024 bytes/kB = 1,073,741,800 bytes10
&#8226; The above is a 2GB swap

The tell the sysem its swap:
```
mkswap /swap
swapon /swap
```

&#8226; Add to /etc/fstab:
```
/swap              swap             swap     defaults
```

---

### Post by kpkeerthi on 2008-02-14
```
sudo fsdisk -l
```
```
cat /etc/fstab
```
Open a terminal and run those commands and post the output here.

Lets make sure what you have and we'll proceed from there.

---

### Post by the badger on 2008-02-16
[COLOR="Blue"]Dirk.R.Gently[/COLOR] -
i ran the first two pieces of code, and then got stuck on adding to /etc/fstab. do i go to the etc/fstab folder and then just copy and paste that piece of code, or do i need to open a file called fstab and edit it?
otherwise very clear. thank you :)

[COLOR="Blue"]kpkeerthi[/COLOR] -
hi. i didn't get your post until i'd gone away with Dirk.R.Gently's.
here's the output (though "-l" wouldn't give me any results with fdisk, with or without sudo. very strange.):
```
badger@clank:~$ fdisk -l
badger@clank:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
badger@clank:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=bd9f1780-9bce-4824-aa72-852a5480ec85 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=4aa8653b-d2b4-48da-b2a4-961769dcbb2f /boot           ext3    defaults        0       2
# /dev/hdb2
UUID=9465f1f6-6e7e-44a0-b349-aa90469c83d6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
badger@clank:~$ 
```

---

### Post by Gen2ly on 2008-02-16
There should be a file already created on installation catt /etc/fstab.  The easiest way to edit it would be to type in the terminal:

```
sudo gedit /etc/fstab
```

The fstab file lists all known devices, partitions, filesystems and their attributes.  This will give you a swap but its not likely to help system performance unless you are really using alot alot of memory.  What does:

```
free -m
```

tell you?

---

### Post by the badger on 2008-02-16
```
badger@clank:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        425         78          0         12        257
-/+ buffers/cache:        155        348
Swap:         1906          0       1906
badger@clank:~$
```

---

### Post by Gen2ly on 2008-02-16
From this I think that the problem isn't with memory.  "free -m" is telling us that only about 250MB is begin used.  How young is your computer?  I ask because I'm thinking that if its a new harddrive there may not be drivers for it yet and is instead using a generic one.

---

### Post by ImAnOgre on 2008-02-28
Jeeze I am so STUPID!!!

I ran the following code:

sudo dd if=/dev/zero of=/swap bs=1024 count=2097152 

however my main partition only had 1gb of space left.... so I tried to delete the file but I can't find it.... ACK.

Can someone help me until I resize the partition and get more space please?

Thanks!!

---

