---
title: "Unusual problems with ntfs-3g"
date: 2006-12-27
forum: General Help
---

### Post by paziek on 2006-12-27
So.. I kinda switched like 2 times between normal ntfs driver (read only) and ntfs-3g.
ntfs-3g was working without any problems so far.. until now. It wont mount my ntfs partitions.
So I did some search, and that what I came up with:


```
modprobe -l | grep fuse | wc -l 

1
```


```
lsmod | grep fuse

fuse                   52500  0 
```


```
apt-cache show ntfs-3g

Package: ntfs-3g
Version: 1:0.20061218-BETA-1
[blablabla]
```

```
sudo apt-cache show fuse-utils

Package: fuse-utils
Source: fuse
Version: 2.6.1-0givre1
[blablabla]
```


I also have versions for fuse 2.5.x installed



```
ntfsmount /dev/hdax /mnt/windows -o fmask=0111,dmask=0 

Couldn't mount device '/dev/hda6': Operation not supported Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
```



```
mount -a

Failed to mount '/dev/hda6': Operation not supported
Mount is denied because NTFS is unclean. Choose one of these actions:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
   the 'force' option read-write, or with the 'ro' option read-only.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
```




```
ntfsfix /dev/hda6

Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.
```


/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/linux1         ext3    defaults,errors=remount-ro 0       1
/dev/hda8 none            swap    sw              0       0
#
/dev/hda5 /media/winprog  ntfs-3g    defaults,locale=pl_PL.utf8   0    0
/dev/hda6 /media/storage  ntfs-3g    defaults,locale=pl_PL.utf8   0    0
#
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


```


So.. this won't work anymore, but with normal ntfs drivers it works ;o

Also, I don't have windows, so I'm unable to use scandisc or whatever windows has.
Question: So why I have ntfs partitions anyways?
Answer: Leftovers after Win XP (had to leave, cous of some god damn undetecable worm sending spam from my PC).


Help:???:

---

