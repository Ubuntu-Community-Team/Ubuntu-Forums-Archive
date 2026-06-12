---
title: "dual boot: directly copy win7 iso to partition from running ubuntu"
date: 2016-07-02
forum: General Help
---

### Post by schnuckenack2 on 2016-07-02
Hello,

I have Win7 32bit and Ubuntu running on the same HDD. Now I hold the Win7 64bit iso on the ubuntu partition. It should be possible to just dd the iso with of={/dev/winpartition}, right? But what about the bootloader and GRUB ? What do I have to do before and after I copied the iso to the respective partition, in order that dual boot will work as usual?

Thanks!

---

### Post by yancek on 2016-07-02
I'm not sure what you are trying to accomplish.  You have a 32bit version of windows 7 along with Ubuntu installed.  Do you now want to install the 64 bit windows 7 to another partition or do you want it to replace the 32bit.  If you have a windows iso file and you want to use it to install the 64bit version of windows 7, you could loop mount the iso in Ubuntu then create an ntfs partition and copy the extracted win 7 folders/files to that partition and put an entry in the Ubuntu grub.cfg file to boot the windows 7 to install.   I used this method to install windows 10 and it should work with 7.  Using dd is certainly not going to give you an installed windows system from the iso it will just give you the install DVD on a hard drive partition.  You might want to clarify exactly what you want to do.

---

### Post by schnuckenack2 on 2016-07-04
> **yancek said:**
> I'm not sure what you are trying to accomplish.  You have a 32bit version of windows 7 along with Ubuntu installed.  Do you now want to install the 64 bit windows 7 to another partition or do you want it to replace the 32bit.  If you have a windows iso file and you want to use it to install the 64bit version of windows 7, you could loop mount the iso in Ubuntu then create an ntfs partition and copy the extracted win 7 folders/files to that partition and put an entry in the Ubuntu grub.cfg file to boot the windows 7 to install.   I used this method to install windows 10 and it should work with 7.  Using dd is certainly not going to give you an installed windows system from the iso it will just give you the install DVD on a hard drive partition.  You might want to clarify exactly what you want to do.
Hello,

I want to *replace* the 32bit version of Win7 on the partition /dev/sda1 - which is an NTFS partition already - with the 64bit version of Win7 on the same partition (/dev/sda1) and *keep the dual boot intact* - via a suitable choice of commands from my running ubuntu installation (on /dev/sda7).

---

### Post by oldfred on 2016-07-04
Probably easier to use Windows tools to create Windows flash drive installer.

But Windows install will overwrite grub in MBR, but it is just a standard repair of grub. 
You can use Boot-Repair or boot Ubuntu live installer and mount your / (root) partition (and /boot if you have one) and install grub to MBR.

 Gui, Terminal & alternate install CD rescue grub repair
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

---

### Post by schnuckenack2 on 2016-07-04
Thank you guys.

The problem I have with the Windows installer is that it doesn't show the partitions like GParted. I don't want ending up overwriting my / or /home partition.

---

### Post by oldfred on 2016-07-04
Windows does not correctly see Linux partitions. Before any major system change, you should update your regular backups.

And if you have your Ubuntu install in a logical partition, it may rewrite partition table without it.
Backup partition table, but then do not make any partition table changes or a restore of backup will restore the old version probably corrupting it.
       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_parts.txt
sudo sfdisk -d /dev/sda > parts_sda.txt

Your reinstall is like the upgrade to Windows 10 and its missing partition issue.
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

---

### Post by yancek on 2016-07-04
> The problem I have with the Windows installer is that it doesn't show the partitions like GParted. 

Doesn't windows show your ntfs partitions with dirve letters?  There won't be any drive letter assigned for any Linux partition.

---

