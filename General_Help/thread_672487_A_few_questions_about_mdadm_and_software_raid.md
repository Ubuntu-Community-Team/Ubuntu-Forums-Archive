---
title: "A few questions about mdadm and software raid"
date: 2008-01-19
forum: General Help
---

### Post by rocktorrentz on 2008-01-19
My home file server is running a 3 disk software raid 5 using mdadm. It's been running for about a year and is working great but there are a few things I don't understand. I set it up using a tutorial which I have lost the url for, it had very little explanation but worked fine.

The first question is why my mdadm.conf says I have a spare disk when I have 3 disks, all of which are in use? Does this mdadm.conf look right to you?
```
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 spares=1 UUID=45d042ca:ff79345d:7bb08481:f2cd1ae2
```

My second question is about the output of "mdadm -D /dev/md0"; what do the minor and major columns mean? I have done a lot of googling to no avail.
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed May 23 07:57:14 2007
     Raid Level : raid5
     Array Size : 586067072 (558.92 GiB 600.13 GB)
    Device Size : 293033536 (279.46 GiB 300.07 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jan 19 22:10:22 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 45d042ca:ff79345d:7bb08481:f2cd1ae2
         Events : 0.21812

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
```

As a bonus, here is the output of "cat /proc/mdstat":
```
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdb1[0] sdc1[2] sda1[1]
      586067072 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>
```

Thanks in advance
rocktorrentz

---

### Post by jpkotta on 2008-01-19
One of the main ways for userspace to access hardware is though device files.  These are all the weird files in /dev/.  The kernel, which actually controls all of the hardware, knows which piece of hardware corresponds to each device file though an attribute of the device file, the *devnum*, which is broken in to a major number and minor number.  All devices of some type (network card, disk drive, USB hub, serial port, etc.) have the same major number, and different instances of such devices have a different minor number (e.g. this serial port is minor 0, whereas that port is minor 1).  If you do ```
ls -l /dev/
``` you can see the major and minor numbers in between the timestamp and user/group.  If you do ```
cat /proc/devices
``` you can see major numbers of some device classes.  

See also: ```
man mknod
```


I don't know about your first question, it confuses me too.  My mdadm.conf has no spares (and there really aren't any).  AFAIK, you don't need mdadm.conf at all.  I never editted it, it just got created on one of my machines, not on another.

---

### Post by fjgaude on 2008-01-19
I guess we are all learning as we go. My cat /proc/mdstat looks like this:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md32 : active raid5 sdb1[0] sde1[3](S) sdd1[2] sdc1[1]
      586067072 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

But I do have a spare and my mdadm.conf file shows it. Notice the sde1[3](S) shows the space, and that is what it is.

One thing I don't understand is the UUID for arrays as shown in the -D command and in the conf file as being different from the one you get when you use vol_id /dev/md0 command.

Thanks to **jpkotta** for the major minor infomation.

Any more help, anyone?

---

### Post by rocktorrentz on 2008-01-20
Ok. I wasn't sure if the majors and minors were something to do with errors, but that's a great explanation. Thanks jpkotta.

I don't appear to have the vol_id command (running on debian). What strikes me as odd is that there are 4 UUIDs for 3 drives; maybe one of them if for the array or something?

---

### Post by fjgaude on 2008-01-20
The array has one for sure as do all devices, period. Do:

```
sudo vol_id /dev/md0
```

for just your array.

---

### Post by rocktorrentz on 2008-01-20
> **fjgaude said:**
> The array has one for sure as do all devices, period. Do:

```
sudo vol_id /dev/md0
```

for just your array.
Sorry to prove you wrong but:
```
sam@samtek:~$ sudo vol_id /dev/md0
Password:
sudo: vol_id: command not found
```

---

### Post by fjgaude on 2008-01-20
That's alright, I'm wrong many a time. You likely don't have volumeid, or vol_id, package installed. It's in Synaptic. Let me know if not.

---

