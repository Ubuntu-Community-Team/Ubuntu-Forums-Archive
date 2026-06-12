---
title: "drive won't show up in /dev"
date: 2008-02-21
forum: General Help
---

### Post by RiTarDid on 2008-02-21
I'm having a problem mounting (or even recognizing) an external ntfs storage drive in usb enclosure on Xubuntu gusty 7.10.  I have 3 identical enclosures containing:
 (2) identical 250gb WD caviar IDE (one of which is the problem drive) 
 (1) Samsung 160gb ide 
all on a powered usb 2.0 hub.  

The 160GB and one of the 250GB's are perfect (automount with ntfs-3g), the other 250GB doesn't even show up in /dev. The drive light was coming on, and I could here the drive spin up and initialize, but ubuntu didn't see a device when I turned it on.  
First,  I switched power sources and cables between all three drives, makes no difference. Then I unplugged the invisible drive from the hub and plugged into another (usb 1.0) port, no change.  So I though the drive was buggered, plugged it into my other xubuntu gutsy (seedbox); the hardware in the two machines is very different but the o/s was installed and set up on both machines simultaneously, so the o/s and installed packages should be nearly identical. The device immediately picked up and mounted on the other machine with no problems.
I don't think it makes a difference, but I'm using ntfs-3g and ntfs-config (i think ntfsprogs is installed too, but i don't know what it does), and mounting smb shares with samba, and fusesmb to see the shares in thunar. Either way; when plugged back into the fileserver, the drive (which should be sdd and sdd1) stubbornly refuses to show up, so i can't mount it anyway.

When all devices are plugged in, turned on and spinning i get this:

dad@files:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 114: ID 55aa:2b00 OnSpec Electronic, Inc. ### 250GB WD
Bus 005 Device 113: ID 55aa:2b00 OnSpec Electronic, Inc. ### 160GB Samsung
Bus 005 Device 108: ID 05e3:0608 Genesys Logic, Inc. 	### hub
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dad@files:~$ fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe8a0598

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0d2e0d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1 



As I said, the drive works perfect when plugged into the linux box beside it, but this one is being ignorant...
Any suggestions?
Thanks in Advance :)

---

### Post by RiTarDid on 2008-03-01
bump

---

