---
title: "Could it be I have NO swap?"
date: 2007-01-19
forum: General Help
---

### Post by psi36 on 2007-01-19
From time to time my PC slows down to almost a complete stop. Last time I checked the system monitor and it showed that I was using almost all available ram. It also showed I was using 0 of 0 available swap. Could it be I don't have a swap partition? And how can I fix this?

[IMG]http://zonk.be/img/System_Monitor.gif[/IMG]

---

### Post by po0f on 2007-01-19
psi36,

Do you remember creating a swap partition during the install?  Post the output of:
```
[FONT="Courier New"]$ fdisk -l[/FONT]
```

---

### Post by psi36 on 2007-01-19
As far as I can remember I did a normal install, so I thought a swap partition was created automatically. 
My second and third drive still have partitions from previous installs of Ubuntu and Debian. I don't use those anymore, just haven't gotten around to getting my files off and repartitioning those disks.
```
$ fdisk -l

Disk /dev/sda: 1050 MB, 1050526208 bytes
33 heads, 61 sectors/track, 1019 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      386556      953625   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(386555, 11, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(953624, 6, 61)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       83801     1045563   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(83800, 2, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1045562, 23, 53)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      928903     1890666   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(928902, 28, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1890665, 16, 36)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?     1433523     1433551       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1433522, 22, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1433550, 8, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by jimbob on 2007-01-19
Issue the [COLOR="RoyalBlue"]top[/COLOR] command from a terminal.

The fifth line down will show your swap size and usage.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by taurus on 2007-01-19
> **po0f said:**
> psi36,

Do you remember creating a swap partition during the install?  Post the output of:
```
[FONT="Courier New"]$ fdisk -l[/FONT]
```

You need to include the sudo in front or you get nothing in return.

```
sudo fdisk -l
```

---

### Post by psi36 on 2007-01-19
Looks like I indead don't have any swap:```
$ top

top - 20:23:01 up 5 days,  6:18,  2 users,  load average: 0.65, 0.68, 0.94
Tasks: 121 total,   5 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.7%us,  4.3%sy,  0.3%ni, 63.0%id,  0.7%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:    516056k total,   508168k used,     7888k free,     3908k buffers
Swap:        0k total,        0k used,        0k free,   123164k cached

```

This is the good fdisk -l:```
$ sudo fdisk -l
Password:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30213   242685891   83  Linux
/dev/hda2           30214       30401     1510110    5  Extended
/dev/hda5           30214       30401     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4985    40041981    b  W95 FAT32
/dev/hdb2            4986       19574   117186142+   b  W95 FAT32
/dev/hdb3   *       19575       21913    18788017+  83  Linux
/dev/hdb4           21914       24792    23125567+   5  Extended
/dev/hdb5           22007       22759     6048441   83  Linux
/dev/hdb6           22760       22849      722893+  82  Linux swap / Solaris
/dev/hdb7           22850       24792    15607116   83  Linux
/dev/hdb8           21914       22006      746959+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4982    40017883+   7  HPFS/NTFS
/dev/hdd2            4983        9868    39246795   83  Linux
/dev/hdd3            9869        9964      771120    f  W95 Ext'd (LBA)
/dev/hdd5            9869        9964      771088+  82  Linux swap / Solaris

Disk /dev/sda: 1050 MB, 1050526208 bytes
33 heads, 61 sectors/track, 1019 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      386556      953625   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(386555, 11, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(953624, 6, 61)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       83801     1045563   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(83800, 2, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1045562, 23, 53)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      928903     1890666   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(928902, 28, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1890665, 16, 36)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?     1433523     1433551       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1433522, 22, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1433550, 8, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by mcduck on 2007-01-19
I've seen couple of posts here where swap wasn't working for some reason.

Anyway, try running 'sudo swapon -a'

Or if that doesn't work 'sudo mkswap /dev/sda6' and then again 'sudo swapon -a' (replace /dev/sda6 with the partition you have for swap)

edit: by the way, all your linux installs can use the same swap partition.

---

### Post by taurus on 2007-01-19
What does your /etc/fstab look like anyway?

```
cat /etc/fstab
```

---

### Post by psi36 on 2007-01-19
Looks like that helped. Now I have 1510068k total swap according to top:
```
$ sudo mkswap /dev/hda5
Setting up swapspace version 1, size = 1546313 kB
no label, UUID=b5c7a7d9-d245-4e58-949c-3fc0163daa61
$ sudo swapon -a
$ top

top - 20:36:11 up 5 days,  6:31,  2 users,  load average: 0.63, 0.70, 0.76
Tasks: 121 total,   3 running, 118 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  1.0%sy,  0.0%ni, 89.0%id,  0.0%wa,  0.0%hi,  4.7%si,  0.0%st
Mem:    516056k total,   504808k used,    11248k free,     4300k buffers
Swap:  1510068k total,        0k used,  1510068k free,   116136k cached
```Thanks mcduck!

---

### Post by psi36 on 2007-01-19
My cat /etc/fstab:```
$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=ef10a09e-eb5f-42b9-9c06-e9669977d300 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=774bcd9a-56f8-424c-8fc8-2ece4566e15e none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# old drives
/dev/hdb2       /mnt/hdb2       vfat    user    0       0
/dev/hdb3       /mnt/hdb3       ext3    user    0       0
/dev/hdb5       /mnt/hdb5       ext3    user    0       0
/dev/hdb7       /mnt/hdb7       ext3    user    0       0
#/dev/hdd1      /mnt/hdd1       ntfs    user    0       0
/dev/hdd2       /mnt/hdd2       ext3    user    0       0
```

---

### Post by taurus on 2007-01-19
Edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line
```
UUID=774bcd9a-56f8-424c-8fc8-2ece4566e15e none swap sw 0 0
```
with this line.
```
/dev/hda5   none   swap   sw   0   0
```
Then, add these lines below it.
```

/dev/hdb6   none   swap   sw   0   0
/dev/hdb8   none   swap   sw   0   0
/dev/hdd5   none   swap   sw   0   0

```
Save it and reboot.  Now, you have so much swap space you don't know what to do with it.  ;)

---

### Post by psi36 on 2007-01-19
Tnx taurus!

---

### Post by taurus on 2007-01-19
So how many GB of swap space you have now? :) 

```
free
```

---

### Post by psi36 on 2007-01-20
3.6 Gig according to my System Monitor. Off which I'm using 4% right now.

---

