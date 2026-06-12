---
title: "Problem with boot manager"
date: 2018-03-27
forum: General Help
---

### Post by damc2 on 2018-03-27
Hello.

I have installed Windows, after that I have installed Ubuntu. I logged in to Ubuntu, everything was ok. Then I logged in to Windows and after that Ubuntu boot manager was gone, I couldn't get into Ubuntu. In order to fix this, I clicked something stupid in Windows like "Solve problems with booting" which probably made the situation worse. I can't boot to Ubuntu, it automatically loads Windows. I can't even go to Bios because Windows is so stupid.

I created something like this with Ubuntu Boot-Repair. They told me to share it with you:

[http://paste.ubuntu.com/p/HHrRvZ74Gk/](http://paste.ubuntu.com/p/HHrRvZ74Gk/)

Are you able to tell me what I should do to fix this basing on this?

---

### Post by yancek on 2018-03-27
You should be able to get into the BIOS regardless of problems on the drive.  Post the manufacturer of the computer or motherboard and someone may have a suggestion.

You have a windows EFI install with 2 EFI partitions which isn't right.  If you can still boot windows, I wouldn't worry about that now.  Since windows is an EFI install, you need Ubuntu as EFI also which it is not or you would have an ubuntu folder on the EFI partition.  Maybe windows deleted it with it's repair.  I would suggest you go to the Ubuntu documentation site below which explains dual booting windows/ubuntu UEFI and use that info to re-install.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Xinghao_Chen on 2018-03-27
I have a Ubuntu 16.04 LTS installed on a USB thumb drive. When I use it with my Lenovo Flex 4 1580 laptop (which uses EFI) I need first to boot the laptop in to Windows 10 and then use the recovery option to select boot from a USB device in order to start Ubuntu.This is because with the newer laptops, BIOS is not accessible at boot time. One must to start Windows first and then in the Settings options to get in to BIOS and make changes. If Ubuntu is the OS you use most frequent, you can change the boot order in the BIOS so your Ubuntu install is the default OS to load when your computer powers on.

I hope this helps.

---

### Post by oldfred on 2018-03-27
Let me guess it is a Lenovo G510. :)

Just so info is in this forum, not the question and answer site.

You have two FAT32 partitions but only one is currently the ESP - efi system partition. Lenovo's seem to do that, and then have the second FAT32 as a way to boot Lenovo repair/recovery programs. They may switch which partition is the ESP when from UEFI you try to do a Lenovo recovery.

I would make sure fast start up is off in Windows, turn off UEFI secure boot and run the fixes Boot-Repair suggests.

These also look like duplicates.

```
Boot000F* EFI USB Device    RC
Boot0015* EFI DVD/CDROM    RC
Boot0016* EFI Network    RC
Boot0017* EFI USB Device    RC
Boot0018* EFI DVD/CDROM    RC
Boot0019* EFI Network    RC
Boot001A* EFI USB Device    RC
Boot001B* EFI DVD/CDROM    RC
Boot001C* EFI Network    RC
Boot0024* EFI USB Device    RC
Boot0025* EFI DVD/CDROM    RC
Boot0026* EFI Network    RC
Boot0027* EFI USB Device    RC
Boot002E* EFI DVD/CDROM    RC
Boot002F* EFI Network    RC
Boot0031* EFI USB Device    RC
Boot0032* EFI DVD/CDROM    RC
Boot0033* EFI Network    RC
Boot0037* EFI USB Device    RC
Boot0038* EFI DVD/CDROM    RC
Boot0039* EFI Network    RC
Boot2001* EFI USB Device    RC
```

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

May be similar?
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

