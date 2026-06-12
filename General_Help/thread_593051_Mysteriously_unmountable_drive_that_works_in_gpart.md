---
title: "Mysteriously unmountable drive that works in gparted?"
date: 2007-10-26
forum: General Help
---

### Post by quiller on 2007-10-26
I have a troublesome drive that holds all my movies. Within gparted, the drive mounts without a problem and works perfectly (as far as I can tell - the files play fine in MythTV). Mounting via command line, though, gives this error:

```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
I haven't found anything in dmesg, but that probably means I don't know what to look for. Still, nothing comes back when running **dmesg | grep /dev/hdb1**, so what gives?

Note that the drive also un-mounts itself randomly. That is, I'll mount it with gparted and my various Myth frontends all work fine. A few hours later and the drive is mysteriously unmounted. The machine(s) in question are all Ubuntu Feisty.

---

### Post by taurus on 2007-10-26
What filesystem is /dev/hdb1?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by quiller on 2007-11-01
The drive is formatted in XFS.

That command outputs this for /dev/hdb:

```
Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       60801   488384001   83  Linux
```

---

