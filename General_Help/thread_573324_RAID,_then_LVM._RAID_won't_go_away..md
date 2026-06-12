---
title: "RAID, then LVM. RAID won't go away."
date: 2007-10-11
forum: General Help
---

### Post by marstein on 2007-10-11
I had two old 300GB disks and put them into this Ubuntu machine (that already had a small 40GB SATA disk). I configured a RAID0 array and it worked well. Then I got another disk and added it to the machine. I thought it would not be possible to increase the size of the RAID array, so I deleted the RAID array (mdadm --stop /dev/md0) and created 3 PVs, VG and the LV from the 3 IDE disks. It worked and I had a 750GB drive! Until the first reboot...
Somehow the RAID array became active again, the LV did not even show up any more. I stopped the RAID again, and tried to remove it from the init.d directory (using sudo update-rc.d -f mdadm-raid remove). Now, with the RAID stopped I still can't see my PVs and so on. The last time I somehow got them back (forgot how) and I could mount the drive but now this just fails:

```
martin@momoputer:/etc/init.d$ sudo mount  -t reiserfs /dev/rootvolgrp/backlv/media/backupdrive
mount: special device /dev/rootvolgrp/backlv does not exist
```

I also tried to put LVM volumes into /etc/fstab with:

```
/dev/rootvolgrp/backlv  /media/backupdrive      reiser  defaults        0      2 
```



My questions: 
how do I remove the RAID array permanently?
Why do my LVM volumes not get started and how do I start them?
How do I put the LVM volumes into fstab?


I am also confused about /dev entries for my hard disks. I had /dev/hda1 and so on. Now there are only hda hdb and hdc and several sd* drives: 

```
martin@momoputer:~$ ls /dev/hd*
/dev/hda  /dev/hdb  /dev/hdc
martin@momoputer:~$ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sdb  /dev/sdd
/dev/sda1  /dev/sda5  /dev/sdc  /dev/sde
```

Finally, maybe it helps, a quote from /var/log/dmesg
```
[   31.007935]  hda: hda1
[   31.028928] hdb: max request size: 512KiB
[   31.028952]  sda1 sda2 <<6>hdb: 586072368 sectors (300069 MB) w/8192KiB Cache
, CHS=36481/255/63, UDMA(100)
[   31.029096] hdb: cache flushes supported
[   31.029116]  hdb: sda5 >
[   31.049093] sd 1:0:0:0: Attached scsi disk sda
[   31.053240] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   31.053346] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   31.054354]  hdb1
[   31.059126] hdc: max request size: 512KiB
[   31.069264] hdc: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255
/63, UDMA(100)
[   31.070204] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   31.070207] Uniform CD-ROM driver Revision: 3.20
[   31.070375] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   31.073773] hdc: cache flushes supported
[   31.073810]  hdc: hdc1
[   31.139923] usb 1-8: configuration #1 chosen from 1 choice
[   31.157952] input: Chicony USB Gaming Keyboard Pro as /class/input/input6
[   31.157965] input: USB HID v1.11 Keyboard [Chicony USB Gaming Keyboard Pro] o
n usb-0000:00:02.0-8
[   31.188852] input: Chicony USB Gaming Keyboard Pro as /class/input/input7
[   31.188880] input,hiddev96: USB HID v1.11 Device [Chicony USB Gaming Keyboard
 Pro] on usb-0000:00:02.0-8
[   31.207837] input: Chicony USB Gaming Keyboard Pro as /class/input/input8
[   31.207843] input: USB HID v1.11 Gamepad [Chicony USB Gaming Keyboard Pro] on
 usb-0000:00:02.0-8
[   31.240280] md: md0 stopped.
[   31.454641] Attempting manual resume
[   31.454645] swsusp: Resume From Partition 8:5
[   31.454646] PM: Checking swsusp image.
[   31.454794] PM: Resume from disk failed.
[   31.466633] md: invalid raid superblock magic on sda
[   31.466638] md: sda has invalid sb, not importing!
[   31.466642] md: md_import_device returned -22
[   31.467083] md: invalid raid superblock magic on sda
[   31.467086] md: sda has invalid sb, not importing!
[   31.467089] md: md_import_device returned -22
[   31.467203] md: bind<hda>
[   31.481187] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.481190] EXT3-fs: write access will be enabled during recovery.
[   31.613003] md: array md0 already has disks!
[   31.820921] md: array md0 already has disks!
```

---

### Post by mohnkern on 2007-10-11
In answer to your last two questions, you put the following in your fstab for logical volumes

<lvm file> <mountpoint> ext3 defaults 0 0 

For example:

/dev/casa/scott /fs/scott ext3 defaults 0 0 


/dev/casa/scott is the logical volume  (casa is the volume group, scott is the logical volume)

/fs/scott is the mount point.

---

### Post by marstein on 2007-10-11
mohncern, that don't work. I listed my fstab entry. I formatted with reiserfs. It's as if the RAID array gets loaded and then LVM may not be able to see it's volume groups...

clueless  :(

---

### Post by marstein on 2007-10-11
Update: I removed mdadm with aptitude and now the volume group is available. It is still not mounted upon bootup so if someone could tell me what's wrong with my fstab line I would appreciate it very much.

```
/dev/rootvolgrp/backlv	/media/backupdrive	reiser	defaults	0	2
```

Does the file system type need to be reiser**fs**?

---

### Post by Jimmy The Clown on 2007-11-19
To remove a RAID effectively, you have to stop the RAID, delete it, and then run the "zero-superblock". Otherwise the hard drive still thinks the RAID exists even if the partitions are not there. Hope that helps.

-JTC

---

### Post by fjgaude on 2007-11-20
> **marstein said:**
> Update: I removed mdadm with aptitude and now the volume group is available. It is still not mounted upon bootup so if someone could tell me what's wrong with my fstab line I would appreciate it very much.

```
/dev/rootvolgrp/backlv	/media/backupdrive	reiser	defaults	0	2
```

Does the file system type need to be reiser**fs**?

Yes.

---

### Post by marstein on 2007-11-23
I have figured out the correct /etc/fstab entry:

```
/dev/mapper/rootvolgrp-backlv /media/backupdrive        reiserfs        defaults        0       0
```

Now the array appears upon boot. It is totally unclear to my why this works.

---

### Post by fjgaude on 2007-11-24
Seems clear enough: you need to have mapper in the device string and you need to have the correct filesystem type spelled correctly. And now you do. Bravo and congrats.

Let the good times roll.

---

