---
title: "Formatted a partition, trying to recover files to boot to Ubuntu"
date: 2015-08-29
forum: General Help
---

### Post by irwan3 on 2015-08-29
Hi,

I have a dual boot system: Windows 8 and Ubuntu 14.04
From Windows, I accidentally formatted a partition that contained files apparently useful for booting to Ubuntu.
I can still boot to Windows but nothing happens when I click on Ubuntu from the grub menu.

I am able to preview the lost files using data recovery tools. I've attached the a screenshot of what the lost files supposedly are.
(There are tons of other files as well but I don't think they're relevant)

How do I recover my files in such a way that I'll be able to boot again to Ubuntu (hoping this is even possible)?

Any ideas?

Thanks.

---

### Post by oldfred on 2015-08-29
If you formatted the entire ESP - efi system partition, you would not have Windows boot files either. Or did you reinstall those?
And you would not be able to get to a grub menu.

You should be able to use Boot-Repair and run the full purge & reinstall of grub2 in advanced mode. You need to boot in UEFI mode so it installs grub-efi-amd64 version.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that is not the solution, post the link to the summary report that Boot-Repair creates.

---

### Post by irwan3 on 2015-09-10
Hi,

Boot repair got stuck in a loop asking me to close all other applications (although it was the only one running).. This seems to be a common issue but it also seems to have many potential different causes so
here is a link to my boot repair info: [http://paste.ubuntu.com/12328218/](http://paste.ubuntu.com/12328218/)

You guys are my only hope !

(also I'm quite a newbie with all this stuff so please make your answer understandable :) )

Thanks in advance

---

### Post by oldfred on 2015-09-10
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots with BIOS boot mode from MBR(msdos) partitioned drives.
But Ubuntu can boot with UEFI or BIOS from gpt drive.
You have gpt, but have grub installed both to the ESP - efi system partition sdb2 and the gpt's protective MBR for BIOS boot. So you may be able to boot either way, but should be only booting in UEFI mode, and reinstalling grub in UEFI mode not BIOS mode. 

For some reason your flash drive is sda. Most systems make flash drive after hard drive and hard drive is sda. You then  have to be careful where you install grub. It normally defaults to install to sda drive, but may overwrite boot loader in installer not install to hard drive.

Microsoft requires a small unformatted partition just before the first NTFS partition. But it looks like you reformatted it to ext4. You need to go back and change it to unformatted. You can use gparted from live installer.
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If dual booting it is important to not have Microsofts fast start up on. That is always on hibernation.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

After you fix the formatting & fast startup, boot Boot-Repair in UEFI mode & reinstall grub (in UEFI mode).

What brand/model system? And what video card chip?
Some brands make it difficult to boot anything other than Windows and some video needs boot parameters until you install a proprietary video driver.

---

### Post by irwan3 on 2015-09-10
Thanks for your quick answer ! 
Fast startup was already off so I'll check the partition issue.
I have a Dell Inspiron 7537 with a Nvidia Geforce..

---

### Post by oldfred on 2015-09-10
Nvidia usually needs nomodeset to boot. If dual video you may be booting with Intel and that is a different parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by irwan3 on 2015-09-16
Hi,

I was looking at what you said on unformatting a small partition for windows but it looks like I already have an unformatted partition before the first NTFS one..
I've attached a screenshot of the disk management on windows for verification.

Again, before I accidentally formatted the partition corresponding to the root / mount point (I followed that tutorial [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) when installing ubuntu) my dual booting was working just fine.

Is it really necessary to make a new unformatted partition before the NTFS one ?! I also wanted to check whether any step that you recommended will lead to some sort of data loss ?

I guess I could also simply reinstall Ubuntu but ideally I'd like to avoid losing my settings.

Again, thanks for your time!

---

### Post by oldfred on 2015-09-16
Have you tried reinstalling grub using Boot-Repair?
Partitions from Windows generally do not make sense to me. It does look like now it at least shows a ext4 partition, but Linux tools show them more correctly.

It looks like your "S:" partition is the reformatted one? It shows "RAW" which in Windows means unformatted. If that is the one you reformatted you may be able to recover it just by using Disks in Ubuntu and resetting (not reformat) to type 07 or NTFS so partition table is correct and maybe using testdisk to restore from NTFS backup the PBR or partition boot sector.
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by irwan3 on 2015-09-16
The S (swap) partition had been like that for a while. I formatted the root partition (R for root..) from ext4 to NTFS :(.
I don't know if there's another option than reinstalling ubuntu..

Boot repair won't work, it is stuck in a loop: [COLOR=#111111][FONT=Consolas]File system repair requires to unmount partitions



[/FONT][/COLOR]

---

### Post by oldfred on 2015-09-16
If you reinstall only use Something Else. See details on why in link below on UEFI.

---

