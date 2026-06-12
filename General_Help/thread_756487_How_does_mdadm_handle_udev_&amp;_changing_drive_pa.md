---
title: "How does mdadm handle udev &amp; changing drive paths?"
date: 2008-04-15
forum: General Help
---

### Post by Bogaurd on 2008-04-15
Hi there,
I've created a few raid arrays on my machine, which seem to be working fine for now.

I'm worried that when I move drives around in the pc (a few are being removed now that the array is up), udev will assign different names (/dev/sdX) to the drives which are members of my raid arrays.

Will mdadm be able to handle this, or am I likely to run into problems?

Cheers!

---

### Post by fjgaude on 2008-04-16
After an array has been created mdadm only uses its own created UUIDs to assemble and run an array.

You can switch out motherboards and the like and the array will still work correctly.

Let us know if you have any issues.

---

### Post by Bogaurd on 2008-04-16
> **fjgaude said:**
> After an array has been created mdadm only uses its own created UUIDs to assemble and run an array.

You can switch out motherboards and the like and the array will still work correctly.

Let us know if you have any issues.

Excellent, that's exactly what I wanted to hear! Thanks! :)

---

### Post by fjgaude on 2008-04-16
Software raid has come a long way since 1992... I've even taken arrays and moved them from AMD to Intel and back without problems... all you do is make sure that mdadm is installed and then:

```
sudo mdadm --assemble --scan
```

And that does it. The --scan checks the superblocks of each drive and from there knows which go with which array, and how to assemble them.

Wonderful!

---

### Post by Bogaurd on 2008-04-19
Alright, I have finished juggling the drives around, but I am having some woes with mdadm.

My raid 5 array of three drives is not being assembled correctly - it's only being assembled with 2 out of 3 drives.

The other drive is visible to the system, even mdadm can see it - if I stop the array, then verbosely reassemble it, this is the output:

```
~# mdadm --assemble /dev/md3 /dev/sdd1 /dev/sde1 /dev/sdf1 --verbose
mdadm: looking for devices for /dev/md3
mdadm: /dev/sdd1 is identified as a member of /dev/md3, slot 0.
mdadm: /dev/sde1 is identified as a member of /dev/md3, slot 1.
mdadm: /dev/sdf1 is identified as a member of /dev/md3, slot 2.
mdadm: added /dev/sde1 to /dev/md3 as 1
mdadm: added /dev/sdf1 to /dev/md3 as 2
mdadm: added /dev/sdd1 to /dev/md3 as 0
mdadm: /dev/md3 has been started with 2 drives (out of 3).

~# mdadm -D /dev/md3
/dev/md3:
        Version : 00.90.03
  Creation Time : Wed Apr 16 11:25:43 2008
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Sun Apr 20 09:56:58 2008
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 536198b8:35e14fe7:117c7856:35374f97
         Events : 0.38

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       2       0        0        2      removed
```


I've tried hot-adding /dev/sdf1, which works, but the whole drive needs to resync then - 500GB, and it's gone again after bootup... I need help! :)

Edit: OK, I've zero'd the superblocks on the array and recreated it now, hopefully this will solve the problem - it's currently resyncing.

One thing I have noticed is that when I examine a partition which is part of an array, the devices contained within the superblock are not necessarily consistent with what devices are actually involved in the array... perhaps someone can shed some light on this.

---

### Post by Bogaurd on 2008-04-20
Okay, I have narrowed this down.

The array is not being assembled with all three drives as one is marked as 'not fresh'.

Looking into it, the timestamp on one disk is shortly after the others after bootup. I've looked through dmesg and found this:

```
[   26.754620] md: bind<dm-6>
[   26.755256] md: bind<dm-7>
[   26.762689] raid5: device dm-7 operational as raid disk 1
[   26.762747] raid5: device dm-6 operational as raid disk 0
[   26.763121] raid5: allocated 3163kB for md3
[   26.763173] raid5: raid level 5 set md3 active with 2 out of 3 devices, algorithm 2
[   26.763234] RAID5 conf printout:
[   26.763282]  --- rd:3 wd:2
[   26.763330]  disk 0, o:1, dev:dm-6
[   26.763379]  disk 1, o:1, dev:dm-7
[   26.832922] ATA: abnormal status 0x8 on port 0x0001b407
[   26.833556] scsi 4:0:0:0: Direct-Access     ATA      ST3500320NS      SN04 PQ: 0 ANSI: 5
[   26.835424] SCSI device sdf: 976773168 512-byte hdwr sectors (500108 MB)
[   26.836170] sdf: Write Protect is off
[   26.836247] sdf: Mode Sense: 00 3a 00 00
[   26.837574] SCSI device sdf: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.838358] SCSI device sdf: 976773168 512-byte hdwr sectors (500108 MB)
[   26.838567] sdf: Write Protect is off
[   26.838688] sdf: Mode Sense: 00 3a 00 00
[   26.838725] SCSI device sdf: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.838806]  sdf: sdf1
[   26.854210] sd 4:0:0:0: Attached scsi disk sdf
[   26.854310] sd 4:0:0:0: Attached scsi generic sg5 type 0

```

The final disk (/dev/sdf) is attached to a PCI SATA controller, as opposed to the other 2 drives connected directly to the motherboard. It looks like it's being detected *after* the array is being assembled.

If I assume correctly, I need to force this drive to be detected earlier... how can this be done though?? :confused:

---

### Post by Bogaurd on 2008-04-20
Alright, I have solved this!

Should anybody else have the same problem, here's what I did:

- Made sure initramfs-tools was installed
- Looked at the output of 'lsmod' once my system was booted to see which modules were active
- Added the modules related to storage to my initrd - by editing '/etc/initramfs-tools/modules', the modules I added were: ata_generic, ata_piix, sata_via, libata
- Generated a new initrd image with 'update-initramfs -k `uname -r` -t -u'

This way my drives (including those on the SATA controller) are detected earlier on in the boot, and are ready to be assembled into arrays :)

---

### Post by fjgaude on 2008-04-20
Wow, interesting... learn something new every day. Thanks for the new knowledge and glad you solved you problem. I would never have thought of it.

---

