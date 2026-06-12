---
title: "The windows IFS swap driver messed up my swap space a bit."
date: 2007-06-03
forum: General Help
---

### Post by the_it on 2007-06-03
Well not really.  When I dual booted this machine, I tried to get windows to read the swap space so that I could locate my paging file there.  But what windows did was it asked to format it as vfat.  Cool with me, I thought, so I let it do that.  Of course, when I booted into linux, Linux wanted to do its own formatting, then it messed up with who's using who, so I decided to just pull the plug on the windows IFS and let linux use it.  Everything's fine now

EXCEPT my Nautilus shows me a 2.0 GB volume under "Computer" (which is my swap space).  It really shouldn't do that.  Right-clicking and checking out properties, then under the Volume tab says that it's still vfat (NO ITS NOT).

```

Label:
Size: 2.0 GB
Media: Hard Disk
UUID: 464C-0A31
File System: vfat (FAT32)
Mount Point: Not Mounted
File System: Not Mounted
Mount Options: Not Mounted

```

And it isn't just some symlink.  Gnome hardware info says its vfat.  Under System->Preferences->Hardware Info:
```
volume.fstype string vfat
volume.fsusage string filesystem
volume.fsversion FAT32
```

Well my swap really is on.
```
markd@trixie:~$ free
             total       used       free     shared    buffers     cached
Mem:       1019564    1010488       9076          0       2460      99476
-/+ buffers/cache:     908552     111012
Swap:      2048276     319760    1728516

```
so it can't be that it's actually vfat.

I thought this was just some funkiness with my partition table.  But my fdisk says that it's also listed as Linux swap!

```
markd@trixie:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5099    20474842+  83  Linux
/dev/sda3            5100        5354     2048287+  82  Linux swap / Solaris
/dev/sda4            5355       19457   113282347+  83  Linux
```

Well it doesnt bug me seriously since I do have swap, but I don't know what's going on.  How do I tell gnome that it isn't vfat anymore?  Or what did windows do that made my linux identify it as vfat?

---

