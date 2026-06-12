---
title: "mdadm RAID mounting"
date: 2007-10-30
forum: General Help
---

### Post by one_million_facets on 2007-10-30
So here I am, on my first serious Ubuntu trial.  I've got the operating system running from an external hard drive (that was fun) and I want to basically use the system as a "server"... but not really... 'cause I'm a n00b.  So I've configured a RAID 1 array with 2 500GB hard drives /dev/sda1 and /dev/sdb1 using mdadm.  So I've created the virtual device /dev/md0 which I then partitioned into an ext3 file system, giving me a - theoretically - mountable /dev/md0p1 to store all my files.  I modified /etc/fstab to include:

> /dev/md0p1     /mnt/raid_system     ext3     defaults     0     0

And I created the /mnt/raid_system directory.

Now when I go to mount the device I get:

> mount: special device /dev/md0p1 does not exist

But running # fdisk -l responds:
> 
Disk /dev/md0: 500.1 GB, 500105150464 bytes
2 heads, 4 sectors/track, 122095984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00045bc6

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1   122095984   488383934   83  Linux

So I know it's there and it does in fact exist.  And not only that, it's active as evidenced by:
> 
root@in:~# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
mdadm: device /dev/md0 already active - cannot assemble it


So now I'm stuck... and I thought I was doing so well too..... any help is greatly appreciated.

---

### Post by fjgaude on 2007-10-30
Looks to me like the array is called /dev/md0, not /dev/md0p1.

Try just the md0 and see what happens.

---

### Post by one_million_facets on 2007-10-30
I tried that at one point. Altered fstab to /dev/md0 and ran:
> 
root@in:~# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Although... that was without a reboot... don't see why that should help though.  But when all else fails...

---

### Post by fjgaude on 2007-10-31
Okay, what does

```
sudo mdadm --deatail /dev/md0
```

and

```
sudo mdadm --assemble --scan --verbose
```

show?

---

