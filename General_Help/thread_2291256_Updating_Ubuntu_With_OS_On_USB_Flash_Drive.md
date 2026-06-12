---
title: "Updating Ubuntu With OS On USB Flash Drive"
date: 2015-08-18
forum: General Help
---

### Post by scottinpa40 on 2015-08-18
Hi, can anyone tell me if you are able to update Ubuntu while having the OS on a USB flash drive?  I installed the updates and then it asked me to restart the computer to finish installing the updates.  When I restart, I set the boot order to the USB drive but when Ubuntu starts, it doesn't finish the updates.  I have tried to install Ubuntu along with Windows on my internal hard drive but it has been so confusing that I decided to just run it from a USB drive.  Thanks for any help!


-Scott

---

### Post by monkeybrain20122 on 2015-08-18
Well the short answer is no. You didn't really "install" Ubuntu in the usb by the look of it, but you have copied a live iso into the usb and run live session.You can install Ubuntu into the usb like you do in the internal hd and theoretically have all the features but it will be slow (and external hd works a lot better)

The long answer is if you create the live usb with persistence than settings will be saved so if something is upgradable then it will remain upgraded after reboot. Without persistence the usb starts with a clean slate everytime you reboot and forgets everything in the sessions before so "reboot to finish upgrade" obviously won't work.

However bear in mind that NOT all upgrades/installations work in live usb(e.g graphic driver and some system components, kernel etc)  even with persistence. If your upgrade requires reboot to complete it is probably one of those things that just don't work in live session. The live usb is basically for installation and simple use (browsing the web, e,g), trouble shooting, as a demo etc but is not meant to be for real daily use.

---

### Post by scottinpa40 on 2015-08-19
Thanks for the info!  I do want to install Ubuntu and have it dual boot with Windows 7 but after reading many guides on how to do it, all have been confusing and haven't worked  :(

---

### Post by scottinpa40 on 2015-08-19
I just realized that I should have posted this in the Installation section of the forums, sorry about that.  I actually thought that I would have to install the Ubuntu OS on my internal drive along with Windows but you mentioned that I could have Ubuntu run from an external drive somehow?  I have several external drives and could give that a try.  I wanted to see if I could dual boot Windows with Ubuntu and someone had told me that in the "Something else" section of the install, I should leave the NTFS alone.  That's all I have on my 2 TB internal drive (NTFS)  Any ideas?

---

### Post by lag-liam on 2015-08-19
Have you tried following the guide found here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have external drive DEFINITELY backup Windows first. If you have the option do a Windows 7 system image backup (if not already using win 7). If you're using win 8 you can do it using this guide: [http://winsupersite.com/windows-8/windows-8-tip-use-windows-7-system-image-backup](http://winsupersite.com/windows-8/windows-8-tip-use-windows-7-system-image-backup)

---

### Post by oldfred on 2015-08-19
While Windows will not boot from an external drive, Ubuntu works from external drive well. Better is USB3 ports or ESATA, as then nearly as fast as SATA.

Is system UEFI or BIOS? 

I do prefer to partition in advance with gparted also as it is a bit easier with gparted. But you still have to use Something Else but use change button instead of + button to chose / (root), /home. If you create swap in advance it seems to automatically find it. If system is UEFI, be sure to create ESP - efi system partition at beginning of drive. And drive must be gpt partitioned, not old MBR(msdos).

But you do need to use Something Else as you want to keep grub2's boot loader on external drive and leave Windows boot loader on internal drive. All auto install options default install grub to drive that is sda, usually the Windows drive with multiple drives.

Several examples, all essentially the same. But one may make more sense than the other so review a couple.
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by scottinpa40 on 2015-08-20
I have a 4 year old Acer Aspire desktop PC with Windows 7 and it is BIOS.  I actually am now dual booting Ubuntu & Windows 7 now, but I had a problem.  I put the Ubuntu install on my (D) Data partition and it erased my data, which luckily I have a backup of.  I didn't think it would erase it but I learned a lesson!  Thanks for your help and if I have any other problems I will let you know.

---

