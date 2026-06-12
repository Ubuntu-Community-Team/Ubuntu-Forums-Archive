---
title: "USB drive won't mount"
date: 2008-06-04
forum: General Help
---

### Post by Red Penguin on 2008-06-04
Hey, I'm  linux noob. After using my new Xubuntu equipped eeePC for  few hours (including using USB ports) I've discovered that when I plug in my USB flash drive I get the message 'Cannot Mount Drive: Invalid mount option when attempting to mount the volume...'

I don't think I've changed anything, and because of my inexperience with linux I've no idea where to start.

Cheers

JL

EDIT: Should've mentioned, the USB stick is OK it works in my other (windows) laptop

EDIT: dmesg tail gets me```

[  128.020000] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  128.020000]  sdc: sdc1
[  128.024000] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  128.024000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  128.944000] UDF-fs: No VRS found
[  129.140000] Unable to identify CD-ROM format.
[  596.108000] UDF-fs: No VRS found
[  596.188000] Unable to identify CD-ROM format.
[  655.904000] UDF-fs: No VRS found
[  655.980000] Unable to identify CD-ROM format.
```

EDiT 3 (Sorry)

fdisk -l gives me
```
Disk /dev/sdc: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00062165

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984     1983619+   6  FAT16

```

Is the * under 'boot' the reason it won't mount? It was the card I used to install xubuntu on the PC, but it's been formatted since then.

---

### Post by ibuclaw on 2008-06-04
What does you fstab file look like?

```
cat /etc/fstab
```

Paste it up, the problem is most probably in there.

Regards
Iain

---

### Post by bingoUV on 2008-06-04
1. The automatic mount options might have gone wrong somehow (updates, your error etc.). Can you mount it manually? Try this command
```

sudo mkdir /media/temp
sudo mount /dev/sdc1 /media/temp

```

If it works this way, we will then worry about making it work automatically.

2. * under boot cannot be a problem.

3. The dmesg output you mentioned may not be related to this problem. Do a dmesg -c before plugging in your drive. Then plug in the drive. Now do a dmesg -c again. 

-c option clears the dmesg's buffer after printing so you are sure you are not getting messages for some earlier incident.

---

