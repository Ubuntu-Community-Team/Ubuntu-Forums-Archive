---
title: "mp3 player destroyed?"
date: 2007-10-15
forum: General Help
---

### Post by a7RoX on 2007-10-15
hi everyone

my problem is very simmilar to the problem from "Messed up with mp3 player. mp3 player = dead" from Anonii, but a bit different

i tried to download some mp3 files from my player yesterday, but 2 files wont let themselves be copied to my hard disk. so i tried with sudo thunar to move them with superuser permissions and it worked fine.
but know every file on my player was a read only file and the only file i could play while using the player was 1 file which was in no folder.
i browsed the internet, used a few commands (which i unfortunately cant remember) and then the player wasnt even in read only mode, i cant access it at all. for strange reasons it was named sigmatel / whatsoever, but it worked and now i see this icon only in my computer-browse-icon, not on my desktop. when i try to open, it says it cannot be mounted and it cant detect the space (2Gig)

my outputs:

tail -f /var/log/messages

[PHP]Oct 15 15:30:14 ubuntu kernel: [ 3327.857514] usb 2-2: new full speed USB device using ohci_hcd and address 7
Oct 15 15:30:16 ubuntu kernel: [ 3330.378048] usb 2-2: configuration #1 chosen from 1 choice
Oct 15 15:30:16 ubuntu kernel: [ 3330.384090] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 15 15:30:21 ubuntu kernel: [ 3335.388912] scsi 5:0:0:0: Direct-Access     SigmaTel MSCN             0100 PQ: 0 ANSI: 4
Oct 15 15:30:21 ubuntu kernel: [ 3335.399883] SCSI device sda: 994048 2048-byte hdwr sectors (2036 MB)
Oct 15 15:30:21 ubuntu kernel: [ 3335.406870] sda: Write Protect is off
Oct 15 15:30:21 ubuntu kernel: [ 3335.425848] SCSI device sda: 994048 2048-byte hdwr sectors (2036 MB)
Oct 15 15:30:21 ubuntu kernel: [ 3335.432843] sda: Write Protect is off
Oct 15 15:30:21 ubuntu kernel: [ 3335.432850]  sda:
Oct 15 15:30:21 ubuntu kernel: [ 3335.451850] sd 5:0:0:0: Attached scsi removable disk sda
[/PHP]


sudo fdisk

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 45.0 GB, 45020602368 bytes
255 heads, 63 sectors/track, 5473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5473    43961841   83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sda: 2035 MB, 2035810304 bytes
63 heads, 62 sectors/track, 254 cylinders
Units = cylinders of 3906 * 2048 = 7999488 bytes

   Device Boot      Start         End      Blocks   Id  System
[/PHP]

i dont understand why there is nothing under "device boot system, etc"
i tried reformatting it with gparted, which showed my player as dev/sda/ 478.5 mb (should be 2gig !?)
however i wanted to reformat the bit remaining space which was unallocated,selected new and set msdos as labeltype

gparted crashed and further tries ended in the same result

when i start the player i can only see the splashscreen "mp3-player" blinking and thats it

i read that you can use windows to reformat it and copy the firmware on it, but i thought the firmware isnt saved on the flash space and i dont want to reinstall windows....
it only was 40 euros, but i dont want to buy a knew one, so i would be very happy if someone knows how to fix it

---

