---
title: "Grub not recongizing Windows 10 installation on another drive Dual boot"
date: 2019-08-27
forum: General Help
---

### Post by tombo007 on 2019-08-27
Hello all! I currently have two hard drives with Ubuntu installed on one and Windows 10 installed on the other. I have the manually select the drive to boot from in BIOS to select either windows or Ubuntu but i would like to be able to utilize Grub to boot into windows. I have tried to mount my windows 10 partition and run sudo os-prober but still nothing is recognized. I also have tried boot-repair and sudo update-grub  I have included my boot summary from boot repair below, any and all help would be appreciated! Thank you for all your help!

Thank you!!!!

Edit:  Link to the output of boot repair is below!

[http://paste.ubuntu.com/p/RmpjT3qH4p/](http://paste.ubuntu.com/p/RmpjT3qH4p/)

---

### Post by yancek on 2019-08-27
You need to post the link created when running the boot repair software rather than posting the output you have which isn't really helpful.

---

### Post by tombo007 on 2019-08-28
Thank you yancek! I edited my original post to include the link.

---

### Post by yancek on 2019-08-28
> Alternatively, you can retry after activating the [Separate /boot/efi partition:] option. 

> Falling back to read-only mount because the NTFS partition is in anunsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting.)

You can use GParted which is on the Ubuntu install media to set the EFI partition (sda2) as active/bootable.

The second problem is that you left your windows OS hibernated which is the default state.  You need to boot windows and turn off fastboot and anything related to hibernation.  Bear in mind that many windows updates will turn this back on and you will not be asked or notified that it is happening.

After doing this, run sudo update-grub again from Ubuntu.

THis should work although you have mixed an EFI install of Ubuntu with a Legacy/CSM install of windows.  The other option would be to do a Legacy install of Ubuntu by creating a BIOD-Boot partition explained in the boot repair and below.

[QUOTEGPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.][/QUOTE]

---

### Post by tombo007 on 2019-08-29
Hey yancek, so I disabled fast boot and all things related to hibernation in windows but I am unsure how to set the EFI partition as active/boot able. I utilized GParted to add the eps and boot flags to the windows sbd1 EFI partition but now it seems like i have two EFI partitions(sdb1 and sda2). I tried to run sudo os-prober and nothing was out putted and also sudo update-grub seem to have done nothing. I re-ran the boot summary and attached the link below. let me know if I am doing anything wrong!Again thank you for all your help!
[http://paste.ubuntu.com/p/MP3MQwn8Hd/](http://paste.ubuntu.com/p/MP3MQwn8Hd/)

---

### Post by yancek on 2019-08-29
Setting the EFI partition as active/bootable would be done using GParted.  First click on the EFI partition (sda2 in your case) to highlight it, then click on the Partition tab and click Manage Flags and click the check boxes for boot and esp.

Your boot repair output near the top shows sdb1 with the standard windows boot files and below that it shows that partition as EFI.  If you set the boot and esp flags for this partition (sdb1), change it back.   An EFI partition on a 'dos' drive is useless.  Windows won't work as an EFI install unless it is a GPT drive and your windows drive is not.

After making the above changes, reboot Ubuntu and update grub again and watch the output for a windows entry.

---

### Post by oldfred on 2019-08-29
UEFI grub will not boot a BIOS Windows.
Once you start booting in one mode, you cannot switch. Or grub only boots other installs in same boot mode.

UEFI does have a one time reboot to totally reboot the system, but grub does not have that capability. I think rEFInd does, but have no BIOS sytems to test.
Generally best to have all systems in same boot mode.
And if newer UEFI hardware, better to use UEFI installs.

---

### Post by tombo007 on 2019-08-29
Thanks for all the input. So from my understanding, my sbd1 partition on my windows drive is a bios boot-loader for windows and my sda2 EFI partition is for Ubuntu? please correct me if i'm wrong. Could i possibly convert my sbd1 windows bios loader partition to an EFI partition and then I would fully be able to utilize grub?

---

### Post by oldfred on 2019-08-29
As I understand it, converting Windows from BIOS to UEFI is complicated.
You also have to convert drive from MBR partitioning to gpt partitioning which normally will work.
And Windows in UEFI boot mode normally wants additional partitions.

Really good backups required.
Often easier to just reinstall.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
new recovery partition just after main partition, recovery image, winre.wim, is typically between 250-300MB Plus free space
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

Some older threads:
       
 Convert Windows from BIOS/MBR to UEFI/gpt.
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/](https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/)
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)

---

### Post by tombo007 on 2019-08-29
Thank you so much oldfred you really are a guru and a saint for helping  me out! I found this guide below on converting the MBR/Bios partition to  EFI  :[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)  do you recommend following it? I'm going to create a complete system  image of my windows ssd and my other gaming ssd so i can recover it if  all goes wrong before doing this.

---

### Post by oldfred on 2019-08-29
I do not know if I missed it, but it has lots of detail on converting from MBR to gpt, but then you have to reinstall or install a Windows UEFI boot loader. I have never done that.

Make sure you create a Windows repair flash drive. 

If you add an ESP which is absolutely required, not sure if then system reserved & recovery are required or optional.
I would expect at minimum you would have to run the set of Windows command to repair an install. 
Windows does use different boot files for BIOS & UEFI. More are in the ESP.

       Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

