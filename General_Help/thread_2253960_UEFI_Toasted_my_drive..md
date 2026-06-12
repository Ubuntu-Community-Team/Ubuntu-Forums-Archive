---
title: "UEFI Toasted my drive."
date: 2014-11-23
forum: General Help
---

### Post by jwfox on 2014-11-23
tl;dr, = partition tables corrupted, don't care about the data, just want my drive back so I don't have to buy a new one.

-=-=-=-=--=-=-=-=-=-=-=-=-=-

I've searched far and wide around the internet, but my google-fu apparently blows rabid walruses.
Is it walruses, or walrii? Are they even susceptible to rabies? Should I be worried? Probably not, I live a fair distance from the coastline, and walrii don't venture this far inland. Plenty of gators, though. Don't care if they're capable of carrying rabies or any other disease, they're gators, dude, jaws and teeth and tail and everything about them is a more immediate concern when faced opposing.

Badgers and possums

Sorry, ADD a bit, I distracted myself.

I don't care about the data, I've got it all backed up, but please hear me out....

I was trying out some different distros by burning live-images to a thumb drive. Somewhere along the line, things went way south of the netherlands, now the 16GB USB drive is reporting that it has 14 GiB... "GiB " is a different thing altogether. So I double-checked it on a MS-Win system, and yup, it claims to have over 140TB avalable.

While I'd love to believe that I had a drive like that on my keychain, it's just too good to be true.

But it's worse than that...

Whatever thing I did wrong with some distro that crapped out my USB drive, it apparently did the same to the HDD in my personal machine whne I tried to boot the live-image. I think with the hours I've spent trying to fix it, I've been working for WAY below minimum wage. Probably easier just to buy a fresh HDD. 

I've spent the last few days chasing this around. I haven't slepft in.... Heck, Since maybe Wednesday? This should be so much simpler than recovering data from the stealthed parts of the drive, I just want to make it useful as a boot-drive again.

Gonna go try not to drink now. Aw, hell, I retract that, nobody's fooled, gonna go drink. But I'll keep hoping someone can teach me how to do it,and understand it.

I'm not interested in data-recovery. If I can get the USB drive back then maybe I can get the HDD back.

Thank y'all for putting up with this rant.

---

### Post by sandyd on 2014-11-23
You can create a new partition table using GParted on the Ubuntu LiveDVD

When opening gparted, you will see something like
[ATTACH=CONFIG]258168[/ATTACH]
On the top-right, change the drive to the correct one (if it isn't already). In this case, it is /dev/sda

If there are "keys" next to the partition (like the ones on in the screenshot), right click and choose 'Unmount'. Start from the last partition on the screen. (in this case, linux-swap)

Then, go to Device -> Create Partition Table.

There, choose GPT

You can do this for your USB drive as well.

Regards,

---

### Post by jwfox on 2014-11-24
Gparted doesn't understand, and thinks it's dealing with 14GiB

---

### Post by jwfox on 2014-11-24
If I wake tomorrow, I will try that.

---

### Post by jwfox on 2014-11-24
No luck...  gparted sees the flash drive as 14.91 GiB (not 'GB', GiB'). It's a 16GB drive. Heck, if it was around ~15GiB, I wouldn't mind, but no.

HDD is 1TB, but gparted shows it as 931.51 GiB. testdisk finds 6 partitions from archlinux that it calls unrecoverable.

[edit:]

sudo sfdisk -f -C3841 -H255 -S32 /dev/sdb
sudo shutdown -r now

.... after reboot ....

No change.

gdisk:
```
Command (? for help): p
Disk /dev/sdb: 31266816 sectors, 14.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 25DE5A43-F9C8-474E-AA41-86263727D386
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31266782
Partitions will be aligned on 2048-sector boundaries
Total free space is 31266749 sectors (14.9 GiB)
```

dmesg:
```
[67465.732076] usb 3-1: new high-speed USB device number 6 using xhci_hcd
[67465.749024] usb 3-1: New USB device found, idVendor=0781, idProduct=5561
[67465.749031] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[67465.749035] usb 3-1: Product: USB
[67465.749039] usb 3-1: Manufacturer:                                
[67465.749042] usb 3-1: SerialNumber: 20052444530EF7F14393
[67465.749421] usb-storage 3-1:1.0: USB Mass Storage device detected
[67465.749607] scsi9 : usb-storage 3-1:1.0
[67466.749499] scsi 9:0:0:0: Direct-Access                               1.03 PQ: 0 ANSI: 2
[67466.750109] sd 9:0:0:0: Attached scsi generic sg2 type 0
[67466.750921] sd 9:0:0:0: [sdb] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
[67466.752136] sd 9:0:0:0: [sdb] Write Protect is off
[67466.752143] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
[67466.752497] sd 9:0:0:0: [sdb] No Caching mode page found
[67466.752500] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[67466.757710] sd 9:0:0:0: [sdb] No Caching mode page found
[67466.757717] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[67466.764754]  sdb:
[67466.765999] sd 9:0:0:0: [sdb] No Caching mode page found
[67466.766006] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[67466.766011] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[67514.810447] usb 3-1: USB disconnect, device number 6
[67530.858837] usb 3-1: new high-speed USB device number 7 using xhci_hcd
[67530.875744] usb 3-1: New USB device found, idVendor=0781, idProduct=5561
[67530.875751] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[67530.875755] usb 3-1: Product: USB
[67530.875758] usb 3-1: Manufacturer:                                
[67530.875761] usb 3-1: SerialNumber: 20052444530EF7F14393
[67530.876148] usb-storage 3-1:1.0: USB Mass Storage device detected
[67530.876325] scsi10 : usb-storage 3-1:1.0
[67531.876199] scsi 10:0:0:0: Direct-Access                               1.03 PQ: 0 ANSI: 2
[67531.876869] sd 10:0:0:0: Attached scsi generic sg2 type 0
[67531.877664] sd 10:0:0:0: [sdb] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
[67531.878788] sd 10:0:0:0: [sdb] Write Protect is off
[67531.878794] sd 10:0:0:0: [sdb] Mode Sense: 03 00 00 00
[67531.879309] sd 10:0:0:0: [sdb] No Caching mode page found
[67531.879316] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[67531.881291] sd 10:0:0:0: [sdb] No Caching mode page found
[67531.881298] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[67531.888289]  sdb:
[67531.889368] sd 10:0:0:0: [sdb] No Caching mode page found
[67531.889372] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[67531.889374] sd 10:0:0:0: [sdb] Attached SCSI removable disk
```

[edit again:]
Yes, it's a crappy 16GB USB drive that really isn't worth the effort, but if I can figure out how to fix it then maybe I can fix my HDD also. I'm booting from a LiveDVD, and I think my DVD drive is getting tired of all the wear-and-tear, but right now it's the only way I can get this machine to work at all.

---

### Post by sandyd on 2014-11-25
Sorry about that, I missed a few things in the first post when I first read it, and I missed the size that Ubuntu said the USB Drive was.
14.9 Gibibyte sounds about right, it converts to approximately 16GB
[ATTACH=CONFIG]258190[/ATTACH]

---

