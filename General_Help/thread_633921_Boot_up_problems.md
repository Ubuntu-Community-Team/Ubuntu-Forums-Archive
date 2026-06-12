---
title: "Boot up problems"
date: 2007-12-07
forum: General Help
---

### Post by battleshipterry on 2007-12-07
I am sure This is a simple fix I am just to new at this to understand what to do.on boot up my Triple boot hangs at.

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=b255ba8a-85f0-429d-87f3-c29dc9cdef3b'

fsck died with exit status 8

to get to desktop I hit enter key and ctrl D then it boots on up fine.this happens everytime I boot.
What is UUID=b255ba8a-85f0-429d-87f3-c29dc9cdef3b ?  Hardware or software I would think a file but I am unsure.
I think fsck is like scandisk in the windblows OS.but agine I am unsure.I am booting Ubuntu,mandriva,and the one Gates is so proud of.This may have been the remains of a triple boot of Ubuntu ,windoze and kubuntu.I got new motherboard and lost the Linux hard drive well had to reload Ubuntu.This is I think the remains of a partition of kubuntu if it is how do I get Grub to boot  and disregard this old partition? Thanks for any help.

---

### Post by PmDematagoda on 2007-12-07
Post the result of:-

```
cat /etc/fstab
```

---

### Post by battleshipterry on 2007-12-07
Thanks for quick response 

ski@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ea6280b-e122-4293-bdc7-e8d10d3ddc69 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=b255ba8a-85f0-429d-87f3-c29dc9cdef3b /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=a94e8129-d329-4cf8-b8e8-082a995013d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
ski@ubuntu:~$

---

### Post by PmDematagoda on 2007-12-07
Here is your problem line:-

```
# /dev/sda3
UUID=b255ba8a-85f0-429d-87f3-c29dc9cdef3b /media/sda3 ext3 defaults 0 2
```

Now could you post the result of:-

```
sudo fdisk -l
```

---

### Post by battleshipterry on 2007-12-07
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dfa2df9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2638    21189703+  83  Linux
/dev/sda2            4644        4865     1783215    5  Extended
/dev/sda3            2639        4643    16105162+  83  Linux
/dev/sda5            4644        4865     1783183+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f04d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

---

### Post by PmDematagoda on 2007-12-07
Ok, now open up the fstab file for editing using:-
```

sudo gedit /etc/fstab
```

And edit the problem line in the following way:-
```

/dev/sda3 /media/sda3 ext3 defaults 0 2
```

After that is done, save the file and then see if the problem is solved.

---

### Post by battleshipterry on 2007-12-07
Oh yea I have been living with that boot up problem for a long time Thanks it is booting great now wow that was a quick fix.That was a problem I must have created when I got new motherboard and tried to run the triple boot I had on old motherboard. Linux and windows don't like changing that much hardware at same time. thanks, well its getting late I should get some sleep it is 1 am here. Thanks very much.

---

### Post by battleshipterry on 2007-12-07
nice hat on penguin  tomorrow I will work on a hat for my wolf a nice festive look.Thanks again.

---

### Post by PmDematagoda on 2007-12-07
Glad to have helped, and thanks for the compliment:), and I wish you good luck with getting your wolf to join the festivities:).

---

