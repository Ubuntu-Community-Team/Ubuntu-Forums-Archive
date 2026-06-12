---
title: "Remove Ubuntu"
date: 2013-04-13
forum: General Help
---

### Post by Shipoopi on 2013-04-13
Hi, a month ago i bought an Asus k56ca notebook.
It came pre-installed with W8 and i wanted a dual-boot system with Ubuntu.
After installing Ubuntu i was unable to boot into W8 again. I tried solving this with boot-repair and asked members from this forum how i could fix it, but nothing seems to work.

([http://ubuntuforums.org/showthread.php?t=1769482&page=96](http://ubuntuforums.org/showthread.php?t=1769482&page=96))

At this point i just want to remove Ubuntu and only have W8.

I just don't know how i would go about doing that. I'm still a beginner at working with Ubuntu.

Thanks

---

### Post by TheFu on 2013-04-13
> **Shipoopi said:**
> Hi, a month ago i bought an Asus k56ca notebook.
It came pre-installed with W8 and i wanted a dual-boot system with Ubuntu.
After installing Ubuntu i was unable to boot into W8 again. I tried solving this with boot-repair and asked members from this forum how i could fix it, but nothing seems to work.

([http://ubuntuforums.org/showthread.php?t=1769482&page=96](http://ubuntuforums.org/showthread.php?t=1769482&page=96))

At this point i just want to remove Ubuntu and only have W8.

I just don't know how i would go about doing that. I'm still a beginner at working with Ubuntu.

Thanks

How did you install Ubuntu? Did you create new partitions or attempt to use wubi?  Which version / release of Ubuntu did you install?
FWIW, Windows8 and the new hardware demanded by Microsoft for that "certified for Win8" sticker broke lots of things for every other OS.  

The shortest answer to your problem might be to reload the entire system using the original Windows8 DVD.  Then again, it might be really trivial to just delete the Ubuntu partition and run the Win8 recovery mode too. We can't tell, yet.

---

### Post by Shipoopi on 2013-04-13
Hi, thanks for the reply.

I installed ubuntu 12.04 from a USB stick on a separate partition.

---

### Post by ajgreeny on 2013-04-13
You will need to restore the Win8 bootloader system before you remove the Ubuntu partitions as if not you will find that grub gives errors, having no configuration files to read and act upon.

If you have a Win8 DVD you can boot to that and repair the bootloader so search for details of how; I do not use windows of any sort any more and can not help with details.  Whatever you do, **DO NOT** simply delete the Ubuntu partitions before you have repaired the Win8 bootloader or you will not be able to boot the machine at all.

---

### Post by oldfred on 2013-04-13
You should just be able to go into UEFI and choose to boot Windows. Some only boot Windows with secure boot on.

If you ran Boot-Repair multiple times, it finds many Secure boot systems have modified UEFI code to only boot Windows and the work around is to rename the Windows boot file. You can use Boot-Repair to unrename or manually copy an original Windows boot files back into the efi partition. Then choose Windows from UEFI menu.

 Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

      
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
**To undo & to rename files** to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by TGM91 on 2013-04-26
Hi,

I tried many times to install Ubuntu on may Sony Vaio SVZ1311. It came with seven pro 64. I removed it in order to try W8 that needs an UEFI boot.
The first time I installed Ubuntu, i can't boot on nothing. On my SVZ, I have remove the "fake Intel Raid 0". So I've 2 disks, sda and sdb, 128 Go *2.
I tried with Linux Mint, same problem but ... the PC booted on Mint only. After repairing the boot loader, I had W8 only.
I tried again with Ubuntu remix (boot repair integrated). During the installation process, the live CD (USB) recognize the UEFI directory. Boot Repair is unable to fix the boot options. I suppose that "something is tagged ?". I will try with 13.04 this WE if possible.
Remarks : the first disk (sda) is in GPT mode, the second on (SDB) in MBR mode.

---

### Post by oldfred on 2013-04-26
You need both drives either MBR(msdos) or both gpt so you can easily have either UEFI with gpt or BIOS with MBR. And both systems need to be the same either both UEFI or both BIOS.

If you had RAID then drive has meta-data on drive.
       > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by TGM91 on 2013-05-17
Hi, sorry for the delay.
Finally, I finished to have an Ubuntu operational !
I got an error with grub : no such device (for the line with W8). I found the answer on an archilinux forum.
You'll find the solution I tried here : [http://forum.ubuntu-fr.org/viewtopic.php?id=1200271](http://forum.ubuntu-fr.org/viewtopic.php?id=1200271), last post.
You have to modify the file 40-custom in the /etc/grub.d directory. After that, it works (UEFI, W8 and Ubuntu) but ...
* the  trackpad doesn't work well,
* the electric consumption is very high (1:30 1:50 seeing a movie with VLC, wifi et network off)
I didn't try the pmd, the blue-tooth, ...
The dual screen works well with the HD4000 driver.
I'm not sure modifying the options for grub with "i915.i915_enable_rc6=1 pcie_aspm=force" in the  ligne GRUB_CMDLINE_LINUX (file /etc/grub/default) will work, the svz1311 have an Ivy bridge chipset.
Note : it seems this option is not necessary for Ubuntu, but the tests on an "old svz11" indicate the contrary ?
Please look here : [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html), middle of page, kernel boot option and here : [http://forum.ubuntu-fr.org/viewtopic.php?id=646001&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=646001&p=1), KeeRool's post, middle of page.

If you have others options ... or suggestions 
Regards

---

