---
title: "Adding software Raid to existing installation"
date: 2005-05-20
forum: General Help
---

### Post by tozzer on 2005-05-20
I'm trying to setup software RAID-1 on an existing installation, using the method of 
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/hdd1
which works fine and I can format the resulting /dev/md0 with ext3.
However, when I reboot I can't mount /dev/md0 (it does exist though)
I then have to reassemble the array with 
mdadm --assemble /dev/md0 /dev/hdd1
and everything works fine, ie I can mount it etc.
I can't understand why it needs assembling after every reboot. I have searched on these forums and on google for answers and nothing seems to work for me. I have used dpkg-reconfigure mdadm to make sure mdadm starts at boot and also dpkg-reconfigure linux-image-2.6.10-5-386 to update the initrd with the currently mounted md devices, but nothing seems to work. I would eventually like to boot off the RAID device, but at the moment I can't even get it to mount automatically. There are no RAID/md related errors in dmesg, and no attempt to make the array either.

Any help would be much appreciated.


Christopher

---

### Post by nad on 2005-05-20
man md

You need to pass the kernel parameter: md=n,dev,dev,...

on the boot line.

---

### Post by tozzer on 2005-05-20
Still no joy to my lilo.conf I added
    append="md=0,/dev/hdd2 md=1,/dev/hdd3"

and now after reboot from dmesg 
Kernel command line: auto BOOT_IMAGE=Linux ro root=302 md=0,/dev/hdd2 md=1,/dev/hdd3

but then

root@server:~# cat /proc/mdstat 
Personalities : [raid1] [raid5] 
unused devices: <none>

I'm starting to think that maybe a clean install is the only way to go.


Christopher

---

### Post by nad on 2005-05-20
You've got only one device listed in each of your raid configurations! Where does /dev/hdd1 fit in? And why are you creating a raid from two partitions on the same drive?

I see your missing device configuration, but this makes no sense.

---

### Post by tozzer on 2005-05-20
Basically, this is what I am trying to achieve:

I have my current linux installation on hda and a blank HD in hdd. 
I want to create a RAID-1 array for two drives but to start with only have hdd in the array. Then I want to copy all my data from hda to the md device (only on hdd), and then boot to hdd. Once this is verified working, I can delete everything on hda, and bring it into the array, giving me software RAID-1 hopefully without any data loss.

However, at the moment I can't get my md devices to mount on boot, so I am not very hopeful about being able to boot onto it.


Christopher

---

### Post by nad on 2005-05-20
What is the contents of /etc/mdadm/mdadm.conf ?

Forget the second raid for now (md1?) and shouldn't your boot command be: append="md=0,/dev/hdd1" ?

---

### Post by tozzer on 2005-05-20
My mdadm.conf is as follows:

```

DEVICE /dev/hda* /dev/hdd*
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=55f46660:23852c1f:766b5999:f7c140cc
   devices=/dev/hdd2
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=27d15152:cefe317f:91c7176e:d2e3aa64
   devices=/dev/hdd3

```

and my partitions are as follows:

```

root@server:~# fdisk -l

Disk /dev/hda: 17.2 GB, 17247928320 bytes
255 heads, 63 sectors/track, 2096 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          30      240943+  83  Linux
/dev/hda2   *          31        1854    14651280   83  Linux
/dev/hda3            1855        1872      144585    6  FAT16
/dev/hda4            1873        2096     1799280   82  Linux swap

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1          19        9544+  83  Linux
/dev/hdd2   *          20       31021    15625008   fd  Linux raid autodetect
/dev/hdd3           31022       32959      976752   fd  Linux raid autodetect

```

I didn't think that the contents of mdadm.conf would matter too much, as I would like to eventually boot off RAID, when this file couldn't be read.


Christopher

---

### Post by nad on 2005-05-20
From the mdadm manpage:

Normally the array will be started after it is assembled.   However  if
       --scan is not given and insufficient drives were listed to start a com-
       plete (non-degraded) array, then the array is  not  started  (to  guard
       against  usage  errors).   To  insist that the array be started in this
       case (as may work for RAID1, 4, 5 or 6), give the --run flag.

---

### Post by tozzer on 2005-05-20
Where would I specify that if I want it to be started on boot?

---

### Post by nad on 2005-05-20
/etc/modprobe.conf 

You should only need this until the raid is 'complete'.

---

