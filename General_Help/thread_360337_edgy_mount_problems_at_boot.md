---
title: "edgy mount problems at boot"
date: 2007-02-13
forum: General Help
---

### Post by greatshape on 2007-02-13
Hi,

I've upgraded from dapper to edgy last week. 
Since, I notice mount problems at boot from time to time. 
It looks like sometimes (so not always) it doesn't mount any FAT/NTFS drives and smb shares during the boot proces. 
The media:/ dir appears to be empty then. 
a manual "sudo mount -a" mounts the hard drives, but not the smb shares. 
The thing I do at that time is reboot the system, sometimes I have to do it twice or even three times to get everything mounted. 
This is very strange and annoying behaviour.  Could it have something to do with the new fstab layout? 

Many tnx for any help

Steve

---

### Post by DerHesse on 2007-02-13
how does your fstab look like?

---

### Post by Giana on 2007-02-13
Actually I've a very similar problem:

If I read-only mount the partition as ntfs everything is fine, I even get the icon on the desktop

> # /dev/sda2 *ntfs*
UUID=000000004581390B /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=4 6 0       1


If i declare it as ntfs-3g to have rw access, then - after boot - I need to type "sudo mount -a" to have it available. And no icon at all on the desktop.

> # /dev/sda2 *ntfs-3g*
UUID=000000004581390B /media/sda2     ntfs-3g    rw,noexec,auto,nls=utf8,umask=007,gid=46 0       1


---

### Post by greatshape on 2007-02-13
> **DerHesse said:**
> how does your fstab look like?

Like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=7d0f3024-7a43-45b3-8f49-d990fd62a304 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=C4B49CB9B49CB002 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=0F1931CBE145AB81 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hdb3 -- converted during upgrade to edgy
UUID=ABAF-C183 /media/hdb3 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hdb2 -- converted during upgrade to edgy
UUID=8861e9a2-cb30-4c18-ab86-8c4c4b4f3367 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

# mount smb shares
//192.168.2.179/shared /media/smb smbfs uid=1000,gid=1000,auto 0 0

steve@Linux:/etc$

```


Kind regards

---

### Post by DerHesse on 2007-02-13
Wrong UUIDs? 
Try
```
$ ls /dev/disk/by-uuid -lh
```and compare it to the values in fstab.
or 
```
$ blkid
```

or just try the old notation.
/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

---

### Post by greatshape on 2007-02-14
> **DerHesse said:**
> Wrong UUIDs? 
Try
```
$ ls /dev/disk/by-uuid -lh
```and compare it to the values in fstab.
or 
```
$ blkid
```

or just try the old notation.
/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

Hi,

I already changed everything back to the old notation and everything seems to be fine now.
Tnx 4 your reply.

Kind regards,
Steve

---

### Post by DerHesse on 2007-02-14
Fine.
:popcorn:


How did you resolve your smb-mount problem?

---

### Post by greatshape on 2007-02-15
> **DerHesse said:**
> Fine.
:popcorn:


How did you resolve your smb-mount problem?

I didn't need to. It was resolved by restoring the original fstab
Strange actually, because the smb mount line in it hasn't changed.

Kind regards, 
Steve

---

