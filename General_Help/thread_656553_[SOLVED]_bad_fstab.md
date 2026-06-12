---
title: "[SOLVED] bad fstab"
date: 2008-01-02
forum: General Help
---

### Post by skymera on 2008-01-02
when i want to mount my windows (sda1) i get bad line in fstab

```

scott@scott-desktop:~$ sudo mount -a
[mntent]: line 6 in /etc/fstab is bad
scott@scott-desktop:~$ 

```

my FSTAB

```



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5fd7f80f-9994-486f-be65-9cf41172e14a /               ext3    defaults, errors =remount-ro,data=writeback,noatime 0 0       1
# /dev/sda2
UUID=9f87294f-718f-4c97-9124-2dd260b20212 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1   	/media/windows  ntfs-3g defaults   	0   	0

```

ps. i had to add sda1 for myself.
so anything wrong?

---

### Post by foolsh on 2008-01-02
```
# /dev/sda1
UUID=5fd7f80f-9994-486f-be65-9cf41172e14a /   ext3    defaults, errors =remount-ro,data=writeback,noatime 0 0       1
```

is the same as

```
/dev/sda1    /     ext3    defaults, errors =remount-ro,data=writeback,noatime 0 0       1
```

so
```

/dev/sda1   	/media/windows  ntfs-3g defaults   	0   	0
```

is trying to mount the same partition where root is mounted at
"/dev/sda1"  is not where your windows partition is at
Are your sure you have one?

---

### Post by foolsh on 2008-01-02
give me some more info about your setup I'll help as much as I can

things I need to know
1. Is this windows partition on the same harddrive as the one linux is on? ie /dev/sda 
or is in on another harddrive ie /dev/sdb
2. Is this a freash install of ubuntu?

---

### Post by jken146 on 2008-01-02
Foolsh is right.  You can't possibly have both / and Windows on sda1.  Please post the output of this comand: ```
sudo fdisk -l
```

---

### Post by skymera on 2008-01-02
my root is on sdb1

windows is sda

```

scott@scott-desktop:~$ sudo fdisk -l
[sudo] password for scott:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19452   156248158+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5957    47849571   83  Linux
/dev/sdb2            5958        6079      979965   82  Linux swap / Solaris
/dev/sdb3            6080       18241    97691265    f  W95 Ext'd (LBA)
/dev/sdb5            6080       18241    97691233+   7  HPFS/NTFS
scott@scott-desktop:~$ 


```

---

### Post by -Zeus- on 2008-01-02
couldn't the space in "errors =remount" on line 6 be a problem?

---

### Post by chrisccoulson on 2008-01-02
I think the actual problem here is that there is an extra digit at the end of line 6. Line 6 currently reads:
```
UUID=5fd7f80f-9994-486f-be65-9cf41172e14a /               ext3    defaults, errors =remount-ro,data=writeback,noatime 0 0       1
```
but should be:
```
UUID=5fd7f80f-9994-486f-be65-9cf41172e14a /               ext3    defaults, errors=remount-ro,data=writeback,noatime 0 0
```

The fact that it seems that your fstab is configured to mount /dev/sda1 twice shouldn't throw up this error, although I'm not sure what the result would be seeing as you've got two lines trying to mount the same partition but specifying a different fs-type (assuming that /dev/sda1 is UUID=5fd7f80f-9994-486f-be65-9cf41172e14a of course). My guess is that your root filesystem isn't really /dev/sda1, and it's just the comment that is incorrect.

Incidentally, what is the output of:
```
blkid /dev/sda1
```
and
```
mount -l
```

edit: -Zeus- : just seen your comment. I think the space would cause a problem too.
skymera: Having just seen your output of fdisk -l above, it all makes sense now.

---

### Post by skymera on 2008-01-02
in my fstab, wheres sdb??

where my ubuntu is =|

---

### Post by jken146 on 2008-01-02
OK, it's just that there is a commented line that says /dev/sda1 before the / entry.  You might want to change this to sdb1 to avoid confusion.


I agree that the space on line 6 shouldn't be there.

---

### Post by skymera on 2008-01-02
ok i fixed the bad line.

but my windows isnt mounting :(

---

### Post by chrisccoulson on 2008-01-02
> **skymera said:**
> ok i fixed the bad line.

but my windows isnt mounting :(

Does sudo mount -a give an error this time?

---

### Post by skymera on 2008-01-02
no it dosent.

but dosent seem to mount windows.
i try again

---

### Post by skymera on 2008-01-02
ok it mounted.
not showing up on desktop..

not a problem, i like clear desktop.

thanks guyss for leading me in the right direction!

top notch.

---

