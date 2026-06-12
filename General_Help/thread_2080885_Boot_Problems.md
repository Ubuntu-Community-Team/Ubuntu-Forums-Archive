---
title: "Boot Problems"
date: 2012-11-05
forum: General Help
---

### Post by klbmanu on 2012-11-05
I've been trying to boot ubuntu 12.10 and keep receiving error messages. I have tried boot-repair and got this link as a result. [http://paste.ubuntu.com/1334606/](http://paste.ubuntu.com/1334606/)

Can anyone help?

---

### Post by techvish81 on 2012-11-05
> **klbmanu said:**
> I've been trying to boot ubuntu 12.10 and keep receiving error messages. I have tried boot-repair and got this link as a result. [http://paste.ubuntu.com/1334606/](http://paste.ubuntu.com/1334606/)

Can anyone help?


can you boot in to win7.? how you installed ubuntu?  i mean,  which option you selected while install,  ('alongside win7' or 'something else')

problem seems to be with the partitioning.

---

### Post by ctt1wbw on 2012-11-05
I'm sort of having the same problems.  I started using Ubuntu at 4.10 but it's been a few years since I've had it.

I used the option "install alongside Windows" and now for some reason I am not able to even see the GRUB menu.  And I can't remember how to fix it.

For whatever reason, the screen won't show anything at boot up, it's like the screen isn't connected to the computer at the time the GRUB is showing so I don't know what to do to get back to my Windows partition.

---

### Post by klbmanu on 2012-11-06
> **techvish81 said:**
> can you boot in to win7.? how you installed ubuntu?  i mean,  which option you selected while install,  ('alongside win7' or 'something else')

problem seems to be with the partitioning.

Windows 7 is no longer on that machine. Basically at first I used the 'something else' option to install ubuntu alongside Windows 7 which didn't work at all. Grub wouldn't boot and Windows 7 kept giving an error message about not finding the operating system. I tried boot repair and everything which didn't work so I deleted the windows 7 and the ubuntu partition using the live CD and tried installing just Ubuntu which got me to here.

---

### Post by oldfred on 2012-11-06
Your script is showing SFS partitions which is dynamic Windows partitions. Dynamic partitions are Windows proprietary, does not work with Linux and does not even work with some Windows repair tools.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Microsoft's official way to undo dynamic partitions is total backup, erase drive create new basic partitions and restore data.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

You get dynamic partitions by using Windows partition tools to create partitions when you already have the 4 primary partitions. Best to only use Windows partition tools to shrink the Windows partition and use gparted for creating extended and logical partitions.

---

### Post by techvish81 on 2012-11-06
i was in a similiar situation with one of my laptop. it had a similiar kind of partition scheme,   what i did was as posted by 'oldfred'  .

in simple terms- 

took a backup of everything , installed EASUS partition manager,  

erased disk and created a partition for win7 at the beginning of disk as a primary partition.  

booted through ubuntu live cd and created an extended partition after the win7 partition with ext4 fs and other logical partitions inside it for different mountpoints /, /home, swap etc. 

shutdown and reboot with win7 disk and installed win7 on the first ntfs partition.(win7 created another partition for boot,  automatically.  

after win7 was successfully installed booted ubuntu disk and installed it with option 'something else' and selecting the extended partition and its mount-points for installation .    i also selected the 'device for bootloader installation'  normally 'sda' if you want to install both the OSs on the same primary disk.  

at the end it was succesfully set-up as a dual boot.

---

### Post by klbmanu on 2012-11-07
The main problem is I can't get access to either operating system so can you use the EASUS partition manager from a live CD and do it all from there?

---

### Post by oldfred on 2012-11-07
I have never used it, but I believe it has a full CD/ISO download on it software page. 

It seems both vendors are converting to only having the dynamic conversion in the paid upgraded versions, not the free version. There may be other places that still have to older free version available for now.

---

### Post by klbmanu on 2012-11-07
> **oldfred said:**
> I have never used it, but I believe it has a full CD/ISO download on it software page. 

It seems both vendors are converting to only having the dynamic conversion in the paid upgraded versions, not the free version. There may be other places that still have to older free version available for now.

How do I use EASEUS though if I cannot boot into any operating system on the laptop at all? I have the .exe file to run it but no operating system to run it on.

---

### Post by oldfred on 2012-11-07
The .exe version is intended to be installed into Windows. You need the full ISO or liveCD version.

It looks like you have to get the Full Edition of the current version they offer.

> WinPE bootable disk and Linux bootable disk are only available in Full Edition. Check [WinPE bootable disk VS Linux bootable disk]("http://www.partition-tool.com/easeus-partition-manager/bootablecd.htm#I3").

If you are sure you have everything backed up, and your logical partitions still match your physical partitions, test disk may work. I would delete any unused partitions or if just a little data back up and delete as the fewer partitions you have to convert the more likely it is to work.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

### Post by klbmanu on 2012-11-07
> **oldfred said:**
> The .exe version is intended to be installed into Windows. You need the full ISO or liveCD version.

It looks like you have to get the Full Edition of the current version they offer.



If you are sure you have everything backed up, and your logical partitions still match your physical partitions, test disk may work. I would delete any unused partitions or if just a little data back up and delete as the fewer partitions you have to convert the more likely it is to work.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

I booted into the EASEUS disk and the option to fix the disk were blanked out and wouldn't allow me to do anything. The only thing I could do was see that it was actually a dynamic disk.

---

### Post by oldfred on 2012-11-07
If Easus, Parted Wizard or testdisk do not work, then you have to use the method suggested by Microsoft. They make it one click to convert to dynamic, but a total uninstall and reinstall to convert back to basic partitioning. Be sure to have good backups and a way to reinstall Windows.

---

### Post by klbmanu on 2012-11-07
> **oldfred said:**
> If Easus, Parted Wizard or testdisk do not work, then you have to use the method suggested by Microsoft. They make it one click to convert to dynamic, but a total uninstall and reinstall to convert back to basic partitioning. Be sure to have good backups and a way to reinstall Windows.

As I said before, I cannot boot into any operating system so would not be able to use the method suggested by Microsoft. I am using another solution I found on another website.

---

### Post by oldfred on 2012-11-07
You cannot delete partitions from the system you are booted into. You have to use gparted from a LiveCD or a Windows repairCD is you want to use Windows.

---

### Post by klbmanu on 2012-11-08
> **oldfred said:**
> You cannot delete partitions from the system you are booted into. You have to use gparted from a LiveCD or a Windows repairCD is you want to use Windows.

I used a liveCD and used gparted to delete all partitions on the disk before putting en ext4, swap and ntfs partition on there. I am now getting the error "bootmgr is missing" when trying to boot into Linux (the only OS currently installed). How can I completely wipe the hard drive and change it back to a basic disk?

---

### Post by oldfred on 2012-11-08
You must still have a Windows boot loader in the MBR. Bootmgr is from Windows. If you have Windows installed make sure the boot flag is on the NTFS Windows primary partition. A Windows bootloader just jumps to the NTFS partition with the boot flag and looks for reference to which boot file to use - bootmgr if Vista/7 or ntldr if XP. 

When you installed Ubuntu did you tell it to install grub2's boot loader to the MBR of the drive or sda not sda1 or sda2?

Boot-Repair can fix it without reinstall or you can use Ubuntu installer and run several commands to install grub2 to MBR.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

