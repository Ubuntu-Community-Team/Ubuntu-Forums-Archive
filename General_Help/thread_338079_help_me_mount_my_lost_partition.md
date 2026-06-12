---
title: "help me mount my lost partition?"
date: 2007-01-13
forum: General Help
---

### Post by bone2006 on 2007-01-13
I orignally have two NTFS with windows XP before going to linux.  Well I originally created a small partition of around 40 megs for ext3.  After awhile I booted up with gparted and created another partition with about 8 gigs, but now when I check I have all these listed.
I was only expecting to see:
Swap
2 NTFS
2 Ext3

I'm not sure what the extended is and I'm not sure which one has my operating system (ubuntu) and not sure if an extra partition was created that I didn't want?  When I run gparted while running ubuntu I see that sda7 and sda8 are not locked.  Does this indicate that the operating system should be on sda3?  I don't want to delete something I'm not supposed to, but right now I only want 2 NTFS and 2 EXT3 (1 Ext3 being the OS) and of course Swap.

Thanks in advance


/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       35853   211190490    f  W95 Ext'd (LBA)
/dev/sda3           35854       38913    24579450   83  Linux
/dev/sda5            9569       35718   210049875    7  HPFS/NTFS
/dev/sda6           35720       35853     1076323+  82  Linux swap / Solaris
/dev/sda7            9562        9568       56164+  83  Linux
/dev/sda8           35719       35719        8001   83  Linux

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Add these three lines to the end of it.

```

/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   ntfs   nls=utf8,umask=0222   0   0
/dev/sda7   /media/sda7   ext3   defaults   0   1
/dev/sda8   /media/sda8   ext3   defaults   0   1

```
Save it.  Then run

```
sudo mkdir /media/sda1 /media/sda5 /media/sda7 /media/sda8
sudo mount -a
df -h
```

---

### Post by bone2006 on 2007-01-14
thanks so much for the help

---

