---
title: "Very long boot after update to 2.6.20-16-generic"
date: 2007-06-14
forum: General Help
---

### Post by earth_walker on 2007-06-14
After the update to 2.6.20-16 on Feisty(x86), my computer started taking about 5 minutes to boot, and failed to mount one of my partitions. On checking out dmesg and fstab, I found that all of my harddrives were renamed from hd** to sd**, and so I had to change a name in fstab and the partition mounted fine. 

However, the boot still takes ages. dmesg shows multiple instances of this:

```
[  241.314886] sdc: Spinning up disk.......................................................................................................not responding...
[  341.948242] sdc : READ CAPACITY failed.
[  341.948244] sdc : status=1, message=00, host=0, driver=08 
[  341.948247] sd: Current: sense key: No Sense
[  341.948250]     Additional sense: Defect list not found
[  341.949930] sdc: Write Protect is off
[  341.949933] sdc: Mode Sense: 00 40 00 00
[  341.952362] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  341.960907] sdc: Spinning up disk......<6>lp0: using parport0 (interrupt-driven).
```

which looks like it's getting into a loop of trying to spin up /dev/sdc. But as far as I know, there is no sdc. There certainly wasn't an hdc before the names were changed. 

I have confirmed that during the boot process it is indeed during the '...' lines that the boot process is hanging.

My fstab now looks like (with uuids obscured):
```

proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=xxxxx643-40bd-4527-9605-3189094a01e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=xxxxx124-7831-46d6-8383-997210a4cda3 /home           ext3    defaults        0       2
# /dev/hdb5
UUID=xxxxx2d9-d146-420c-8551-42c4dea9e454 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda3	/home/me/documents	vfat umask=0000 0 0
```

So what has changed? why is it looking for sdc when it's not in fstab? How do I stop this behaviour?

On a side note, this is a production machine. Looking at the forum, although no-one has my particular problem, this update crashed lots of other computers. Does this mean I shouldn't be updating kernels even though this is supposed to be a stable release? Should I trust any updates at all? When can I trust an update? Should I just be doing security updates?

---

