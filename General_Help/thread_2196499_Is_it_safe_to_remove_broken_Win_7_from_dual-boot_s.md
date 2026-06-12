---
title: "Is it safe to remove broken Win 7 from dual-boot system?"
date: 2013-12-29
forum: General Help
---

### Post by kdelwat on 2013-12-29
When I boot into Windows 7 from grub, I get an UNMOUNTABLE_BOOT_VOLUME error. However, I can still boot fine into Ubuntu. Is it safe to just delete Windows 7?

This is the output of "sudo fdisk -l".
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe8816e73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   319989759   159993856    7  HPFS/NTFS/exFAT
/dev/sda2       319989760   720283695   200146968    7  HPFS/NTFS/exFAT
/dev/sda3       894257152   976773167    41258008   83  Linux
/dev/sda4       720285694   894255103    86984705    f  W95 Ext'd (LBA)
Partition 4 does not start on a physical sector boundary.
/dev/sda5       884492288   894255103     4881408   82  Linux swap / Solaris
/dev/sda6   *   720285696   884492287    82103296   83  Linux

Partition table entries are not in disk order

```

Partition contents:
[TABLE="width: 500"]
[TR]
[TD]sda1[/TD]
[TD]Windows 7[/TD]
[/TR]
[TR]
[TD]sda2[/TD]
[TD]Data[/TD]
[/TR]
[TR]
[TD]sda3[/TD]
[TD]Failed Linux From Scratch Installation[/TD]
[/TR]
[TR]
[TD]sda4[/TD]
[TD]Extended partition containing:[/TD]
[/TR]
[TR]
[TD]sda5[/TD]
[TD]Swap[/TD]
[/TR]
[TR]
[TD]sda6[/TD]
[TD]Ubuntu[/TD]
[/TR]
[/TABLE]

The output of [Bootinfoscript]("http://bootinfoscript.sourceforge.net/") is here: [http://pastebin.com/t5NiDKFM](http://pastebin.com/t5NiDKFM)

I hope I've given enough information. Thanks for all help in advance.

---

### Post by monkeybrain20122 on 2013-12-29
Don't see why it would be a problem. Just reformat the Win partition to ext4 then boot into Ubuntu to update grub would do it. The more tricky question is what you plan to do with the vacant space.

---

