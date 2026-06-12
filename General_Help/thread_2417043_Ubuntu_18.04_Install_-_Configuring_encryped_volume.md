---
title: "Ubuntu 18.04 Install - Configuring encryped volumes error"
date: 2019-04-19
forum: General Help
---

### Post by sean772 on 2019-04-19
I'm trying to install 18.04 LTS for the first time. This will also be my first install of an encrypted OS. After I set the security key I get the error: "An error occurred while configuring encrypted volumes. The configuration has been aborted."

I also tried installing alongside my previous distro, 16.04 LTS, but I got the error: "ubi-partman failed with exit code 141"

The bootable usb I am trying to install from was actually made while on a live session on my old 16.04 bootable usb. It was made with the Ubuntu startup disk creator, whereas the 16.04 usb was made with rufus. Finally, this may or may not be related to my problem, but I ran parted and saw some partitions I had never seen before. I would appreciate some recommendations for resources to gain some substantive knowledge about what the partition tables should look like and what the partitions do.


Thanks in advance for any help.

---

### Post by TheFu on 2019-04-21
I don't have any answer, just some things to consider.

Did you verify the installer - should be an option on the first screen to check the install disk.

If that is fine, I'd check the SATA cables and drives for errors. There are lots of posts here about failing storage devices and using smartctl to see what the drive will tell us about itself.  This is part of the smartmontools package.  You can install that into a live-boot installer a "Try Ubuntu" session. Anything funny in that data?

Thanks for mentioning the different USB creation techniques. Both of those should work fine. I'm lazy and just use dd or ddrescue when I need a fresh installer on some flash storage to try, fix, or install any Ubuntu system.

As for encryption, I use it all the time.  The default whole drive encryption installations that I've seen/used always wipe the entire disk, setup MBR partition tables (yuck!), create 3 partitions - one for /boot, one for /boot/efi/, and the 3rd for the encrypted storage which fills the rest of the disk. The 1st two partitions use about 1.2G of storage, which is relatively small on disks today.  

The 3rd partition gets encrypted and inside that encrypted container LVM is used to setup a PV, VG, and a few LVs.  This is good because the default installer doesn't setup the LVs with separate /home and leaves the root-LV (for the OS) much too large, IMHO.  

I like to limit the size of the OS / and /home LVs, to help with my backups.  I backup at the partition level.  LVM also allows freezing a "snapshot" so the backups are perfectly quiesced and can be taken on a running system. 

Whenever encryption is involved, having 100% great backups is mandatory.  If/when something bad happens, having a good backup that you know can be restored is the only solution. Please don't skip this part.

---

