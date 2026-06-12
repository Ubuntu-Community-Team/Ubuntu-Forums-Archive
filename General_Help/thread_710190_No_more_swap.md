---
title: "No more swap"
date: 2008-02-28
forum: General Help
---

### Post by ep2011 on 2008-02-28
I just installed arch as a triboot with ubuntu and windows, and I am using the same swap partition for both ubuntu and arch (I can do this, correct?). When I log back into ubuntu, conky says "No swap% 0B/0B". Does this mean I have no swap with ubuntu? How would I go about fixing this?

edit: my swap partition is /dev/sda5

---

### Post by kpkeerthi on 2008-02-28
Open a terminal and type ```
top<enter>
``` and post the output here. It should tell you if swap is being used or not.

---

### Post by kpkeerthi on 2008-02-28
Your fstab might need some minor changes if top finds that swap is not being used.
Post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```  to help fix that.

---

### Post by kpkeerthi on 2008-02-28
> **ep2011 said:**
> 

edit: my swap partition is /dev/sda5

To reset your swap to /dev/sda5 run 
```

sudo swapon /dev/sda5

```

To make the change permanent change swap partition to /dev/sda5 in /etc/fstab

---

### Post by ep2011 on 2008-02-28
> **kpkeerthi said:**
> Open a terminal and type ```
top<enter>
``` and post the output here. It should tell you if swap is being used or not.

> **kpkeerthi said:**
> Your fstab might need some minor changes if top finds that swap is not being used.
Post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```  to help fix that.

> **kpkeerthi said:**
> To reset your swap to /dev/sda5 run 
```

sudo swapon /dev/sda5

```

To make the change permanent change swap partition to /dev/sda5 in /etc/fstab


ok here is my top command (only the part pertaining to swap):
```
Swap:        0k total,        0k used,        0k free,   188068k cached
```

Here is sudo fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d941d93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1194     9586048+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1195       17217   128704747+   7  HPFS/NTFS
/dev/sda3           17218       30401   105900480    5  Extended
/dev/sda5           27661       27790     1044193+  82  Linux swap / Solaris
/dev/sda6           27791       30401    20972826   83  Linux
/dev/sda7           19829       27660    62910508+  83  Linux
/dev/sda8           17218       19828    20972794+  83  Linux

Partition table entries are not in disk order

```

Here is cat etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=37fcf41f-fe3b-4610-81d2-46ad627e237c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=e882cf3c-46c4-46ca-a9f9-5a65930a6d9b /home           ext3    defaults        0       2
# /dev/sda1
# UUID=6BEE-203B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
# UUID=784C63E84C63A01C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=b5dc9f24-0701-4a2d-9828-437320f1f0cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

What I don't get is that it says /dev/sda5. I'd like a permanent change... Thanks

---

### Post by kpkeerthi on 2008-02-28
I'm guessing that UUID of your swap partition has changed (probably when you altered your partition recently?)

You may try chaging the line that reads
```

# /dev/sda5
**[COLOR="Red"]UUID=b5dc9f24-0701-4a2d-9828-437320f1f0cc[/COLOR]** none            swap    sw              0       0

```
to
```

# /dev/sda5
**[COLOR="Blue"]/dev/sda5[/COLOR]**   none         swap    sw              0       0

```

If you prefer to have UUID, find out the UUID of /dev/sda5 using 
```
sudo vol_id -u /dev/sda5
``` and change it accordingly in fstab

To remount the partitions added/changed in fstab immediately without having to reboot run ```
sudo mount -a
``` and you will see errors printed out if any.

---

### Post by ep2011 on 2008-02-29
> **kpkeerthi said:**
> I'm guessing that UUID of your swap partition has changed (probably when you altered your partition recently?)

You may try chaging the line that reads
```

# /dev/sda5
**[COLOR="Red"]UUID=b5dc9f24-0701-4a2d-9828-437320f1f0cc[/COLOR]** none            swap    sw              0       0

```
to
```

# /dev/sda5
**[COLOR="Blue"]/dev/sda5[/COLOR]**   none         swap    sw              0       0

```

If you prefer to have UUID, find out the UUID of /dev/sda5 using 
```
sudo vol_id -u /dev/sda5
``` and change it accordingly in fstab

To remount the partitions added/changed in fstab immediately without having to reboot run ```
sudo mount -a
``` and you will see errors printed out if any.

Still doesn't work... no errors, but both conky and the top command confirm there is still no swap...

I checked arch and /etc/fstab has the same partition for swap, and works.

---

