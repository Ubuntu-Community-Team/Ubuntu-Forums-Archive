---
title: "duplicated /home partition?"
date: 2007-03-13
forum: General Help
---

### Post by sinpalabras on 2007-03-13
hi 
   I was trying to resize my home partition(ext3)  by diminish windows and /root partition (dual boot).I used gparted from a livecd and everything went fine till it stop all off a suden saying that there were read errors, a reboot and find that home is the same size than before butt on /media there is another home partition, is that a mount point? were is the extra space from resizing?

juan@ubuntubox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  5.1G  4.2G  55% /
varrun                376M   76K  375M   1% /var/run
varlock               376M     0  376M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                376M     0  376M   0% /dev/shm
lrm                   376M   21M  355M   6% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1              12G  8.9G  2.9G  76% /media/sda1
/dev/sda5              41G   39G  154M 100% /media/sda5
/dev/sda5              41G   39G  154M 100% /home


/dev/sda1 is windows
/dev/sda2 is edgy 
/dev/sda5 is ?
i dont understand why is listed twice and also my HD is only 80gb. 

If you can help thanks

---

### Post by lloyd_b on 2007-03-13
It is quite possible on Linux systems to have the same filesystem mounted twice, in two different locations.  It appears that "/dev/sda5" is your "/home" partition, and it is also mounted at "/media/sda5".

Could you post the following:
1.  The output from running the "sudo fdisk -l /dev/sda" command
2.  The contents of the file "/etc/fstab"

What I suspect happened is that for some reason you've gotten an extra line in fstab that remounts the /home directory under /media/sda5.  But I'd like to see those two items before I make any recommendations as to what you should do to fix it...

Lloyd B.

---

### Post by sinpalabras on 2007-03-13
juan@ubuntubox:~$ sudo fdisk -l /dev/sda
Password:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531        2805    10241437+  83  Linux
/dev/sda3            3011        9726    53946270    5  Extended
/dev/sda4            2806        3010     1646662+  82  Linux swap / Solaris
/dev/sda5            3011        9726    53946238+  83  Linux

Partition table entries are not in disk order




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=365d4c47-251d-4928-b087-712db5bccb46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2C8CE11B8CE0DFF6 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=d5befce6-3de9-4976-97f2-33e9137b4482 /media/sda5     ext3    defaults        0       2
# /dev/sda4
UUID=71dd9182-e5d3-4955-909f-5676dff3a4d2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5       /home        ext3    defaults        0       0

Thanks Lloydb

---

### Post by sinpalabras on 2007-03-13
should just delete the last line  in /etc/fstab? 
   it would keep my /home as a diferent partition if it's mount in /media? 
   I deleted the home partition on media whit root nautilus script and home disappeared.I had to boot windows and (by chance) move the whole partition from the thash can to 
E: (thats the name of /home in windows) and worked .

---

### Post by lloyd_b on 2007-03-13
Okay, it's pretty much as I suspected.  "/dev/sda5" is the correct partition for your "/home" filesystem, but it's gotten mounted twice.

So, to fix this you need to edit your "/etc/fstab" file.  Note: you must be superuser (root) in order to do this, so in a terminal:
```
gksudo gedit /etc/fstab
```

Change the line
```
UUID=d5befce6-3de9-4976-97f2-33e9137b4482 /media/sda5 ext3 defaults 0 2
```
to
```
UUID=d5befce6-3de9-4976-97f2-33e9137b4482 /home ext3 defaults 0 2
```

And delete the line
```
/dev/sda5 /home ext3 defaults 0 0
```

And when you reboot, that "extra" mount at /media/sda5 should be gone.  This should put your system back to the way it was before you attempted the resize.

I honestly don't know what went wrong with the resize, but I strongly recommend that you have all partitions on the machine backed up before attempting ANY changes to partitions - a glitch during the resize could just have easily have trashed the entire drive!!

Lloyd B.

---

### Post by sinpalabras on 2007-03-13
It worked. 
Thanx a lot  Lloyd B

---

