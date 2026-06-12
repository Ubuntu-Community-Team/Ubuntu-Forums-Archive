---
title: "Uninstalling ubuntu"
date: 2016-06-15
forum: General Help
---

### Post by otto.laari on 2016-06-15
I'm a total noob when it comes to linux. I tried dualboot ubuntu on my laptop, but it wasn't for me. I hastily tried uninstalling it and deleted the partitions from disk management and combined them with my windows 7 main partition _before_ getting rid of grub loader. Now when I try to boot I get the grub rescue screen. I tried [this]("http://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition") with all the partitions that were listed but all of them said no such partitions existed. I also tried boot-repair through ubuntu liveUSB, but nothing changed. [This is the paste]("http://paste2.org/3e3tkpZn") that was created. I tried updating grub, but it doesn't let me and instead says:
> /usr/sbin/grub-probe: error: failed to get canonical path of /cow.
How can I remove grub loader and access windows 7?

---

### Post by yancek on 2016-06-16
You don't "uninstall" operating systems which is what Ubuntu is.  That is only for software applications installed within an operating system.  What you do is to format the partition.  Before formatting the partition, if you have another operating system on the computer, you need to make sure that you can boot it (windows) without using anything from the other system (Ubuntu).  The reason for this  is that there is minimal boot code in the MBR and the rest of the boot code/files are on the partition.  So if you were booting both Ubuntu and windows with Grub, you deleted the boot files without setting the system to boot from windows first.

You can clearly see this in the boot repair output which shows Grub code in the MBR looking for its files on sda5 (msdos5) which clearly does not exist.

The error you got on trying to update-grub is because you ran it from the DVD which won't work.  Actually, you don't have the necessary Grub files so there really isn't any point in trying to reinstall it as you would need to create a partition for it.  You don't want to install it on a windows partition as that will mess up the windows boot files also.  You could reinstall Grub but you would need somewhere to put it and you only have windows partitions.

The standard method of repairing this is to use the repair option on your windows installation DVD.  See post three at the link below for the commands you need to use.  If you don't have a windows installation DVD you will have to do an online search for some software to use to repair it.  I've read that Hiren's boot CD will work but haven't used it myself.

---

### Post by oldfred on 2016-06-16
COW is copy on write or the live DVD which you cannot update. So command gives error.

Best to use your Windows repair flash drive and Windows fixMBR command.
       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If you have working Ubuntu live installer you can add Boot-Repair. It does not do many Windows repairs, but can install a Windows type boot loader. Advanced options let you choose system and drive to update MBR.

You can also install syslinux or lilo boot loaders, manually. Both are Windows type boot loaders.
       
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) 
    

 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 

      
 sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

