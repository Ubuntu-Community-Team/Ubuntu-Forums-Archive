---
title: "Changing GRUB location post-install on 15.04?"
date: 2015-05-30
forum: General Help
---

### Post by oapeter on 2015-05-30
Hello all.

I just finished setting up a triple-boot of Windows 8.1, OpenSuSE and Ubuntu 15.04. When installing Ubuntu, I forgot to change the boot loader install location to the /boot partition I created for it. Instead it has wiped out my Windows loader on sda. 

I can fix the Windows loader with the CD, that's not a problem, but I'd like to change the Ubuntu boot loader installation to the correct place afterwards without doing a reinstall (not that its difficult).

Is this possible?

Otherwise I can just re-install Ubuntu entirely, but I would like to know if there is a better solution first.

Thanks!

---

### Post by oldfred on 2015-05-31
But Windows will not boot Ubuntu. And installing grub to a partition boot sector is not recommended. But if you are using another copy of grub to boot then installing a second grub to a partition is ok becuase it is not really used. Grub installed to a partition forces it to convert to blocklists or hard coded addresses since it otherwise does not fit. But updates or even a fsck can move a file and then address is wrong & grub breaks.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

In your case you may want to choose a partition, but normally not recommended.

---

### Post by oapeter on 2015-06-01
Thanks for the response! Unfortunately I ended up just repairing the MBR with the Windows CD and re-installed Ubuntu.

I have been using the OpenSuSE Grub2 installation as my boot loader. When I install OpenSuSE, I create a primary boot partition and install it's boot loader there. The rest of the drive is an extended partition and that's where i put the rest of the OpenSuSE partitions, as well as Ubuntu's boot partition. 

This leaves the Windows MBR in tact and if there is ever a problem, I just have to use Diskpart in Windows to switch the active partition.

I set it up this way because I found that some Windows Updates would fail unless I switched the active partition back to the Windows primary partition. 

I will keep this bookmarked and use it in the future though. 

Thanks a lot!

---

### Post by oldfred on 2015-06-02
Grub does not use boot flag or active partition. 
You then are using the Windows boot loader to boot to the partition boot sector with grub and that is often an issue for both systems.
Windows has to have boot flag or active partition on the primary NTFS partition with the boot file. And it only repairs, installs into, or boots from the active partition. 
Grub does not use nor need the boot flag to chain load to Windows. So you should be able to boot with grub in MBR, chain load to Windows boot partition to boot Windows, and Windows updates should still work as it will see boot flag on its partition. Sometimes Windows updates do overwrite the MBR, so you want both a Windows repairCD or flash and a working Linux repair flash drive that boots in live mode. Then you can repair either system.

---

