---
title: "[SOLVED] Mount point mix up"
date: 2008-06-27
forum: General Help
---

### Post by krelverehan on 2008-06-27
Okay, so I had this external hard drive formatted as a jfs and working great... This is until I decided to change the mount points from [COLOR="Blue"]Volume Tab[/COLOR] in the Properties menu.

I attempted to change the mount point [COLOR="Blue"]/home/krel/160.0 GB Media[/COLOR].

I also kept the same window rules used when it was mounting fine in [COLOR="Blue"]/media/disk[/COLOR].

Now, it told me that changes won't take effect until I remount the drive. Now when I tried that I got the error:
> [B]
Cannot mount volume.[/B]
Unable to mount volume.
\/Details
mount_point cannot contain the following
characters: newline, G_DIR_SEPARATOR (usually /)

Now, I am pretty sure this error is because I used spaces in the mount point title... How do I change it back?

Here is my [FONT="Courier New"]gksudo gedit /etc/fstab[/FONT] in case it is necessary:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=df54b1eb-9a0a-41c7-9139-be1ae1a09ca7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=21c13a53-fe91-4073-80da-a3e50051dce2 /home           ext3    relatime        0       2
# /dev/sda1
UUID=3a7c0579-61e5-4182-afd8-cee4cca34903 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

My external is usually called sdb1, which doesn't appear in fstab.

Thanks!

---

### Post by russlar on 2008-06-27
I've found that trying to specify mount points in the gui doesn't work. If someone else knows how to make it work, please, share. :confused:

---

### Post by TalioGladius on 2008-06-27
> **russlar said:**
> I've found that trying to specify mount points in the gui doesn't work. If someone else knows how to make it work, please, share. :confused:

Manually mount them in /etc/fstab.  Although my suggestion would be to mount them using the UUID being that the id under /dev tends to change with each reboot.

so here's a sample of my fstab file:

```
#data drive
UUID=88EC90C2EC90AC46	/media/Data	ntfs-3g	defaults	0	0
UUID=0a7ebe21-4add-4372-bd24-7790b968b1a7	/media/Fun	ext3	defaults	0	0
```

---

### Post by krelverehan on 2008-06-27
How would I find my UUID for sdb1?

---

### Post by sisco311 on 2008-06-27
```
sudo blkid
```
or
```
sudo vol_id --uuid /dev/sdb1
```

---

### Post by krelverehan on 2008-06-27
Thank you both! It is up and running again, and mounting from the right spot!

Gorgeous!

Here is what I added to [FONT="Courier New"]/etc/fstab[/FONT] after obtaining my UUID for sdb1 from [FONT="Courier New"]sudo blkid[/FONT]:
```
# dev/sdb1
UUID=ada04434-df6f-40d6-892d-8967c599779f	/home/krel/Storage	jfs	defaults	0	0
```

---

### Post by TalioGladius on 2008-06-27
> **krelverehan said:**
> How would I find my UUID for sdb1?Sorry, didn't mean to leave that out.


```
sudo vol_id -u /dev/sda1
```

---

