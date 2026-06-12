---
title: "Installed Lubuntu, now my Windows 8.1 won't boot"
date: 2014-05-30
forum: General Help
---

### Post by toby5 on 2014-05-30
Hi there, 

My entire time I have been struggling to install Ubuntu because of partitions. Everything I tried met a dead-end which was no good.

Today I tried installing Lubuntu from a CD drive and it all went great as the location I decided to install was /dev/sda. I partitioned it and set up the swap as well.
Now upon rebooting my PC every time I am greeted with the following screen:

[IMG]http://i62.tinypic.com/anzio8.jpg[/IMG]

I am not sure how to fix and any help to fix would be great. I have already tried boot-repair but to no avail.

EDIT: /dev/sda is my SSD

---

### Post by oldfred on 2014-05-30
Instructions for installing include turning off Intel SRT before installing. :)

Also have to turn off Windows fast boot or always on hibernation or you may have major issues. And often better to have secure boot off but not absolutely required. Grub menu may not let you boot Windows with secure boot on, but you can boot both Ubuntu & Windows from UEFI menu.

See if in UEFI/BIOS you can turn off Intel SRT.
Post link to BootInfo report from Boot-Repair.
What system & video do you have.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)

SRT is the same for all vendors.
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

More info on UEFI install with screen shots in first links and Ultrabooks in the link in my signature.

---

### Post by toby5 on 2014-05-30
> **oldfred said:**
> Instructions for installing include turning off Intel SRT before installing. :)

Also have to turn off Windows fast boot or always on hibernation or you may have major issues. And often better to have secure boot off but not absolutely required. Grub menu may not let you boot Windows with secure boot on, but you can boot both Ubuntu & Windows from UEFI menu.

See if in UEFI/BIOS you can turn off Intel SRT.
Post link to BootInfo report from Boot-Repair.
What system & video do you have.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)

SRT is the same for all vendors.
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

More info on UEFI install with screen shots in first links and Ultrabooks in the link in my signature.

My laptop is a Lenovo U310 IdeaPad and here is the boot-repair paste: [http://paste.ubuntu.com/7552233/](http://paste.ubuntu.com/7552233/)

A lot of the tutorials I went on seemed jumbled so I may have missed something but I'm not sure!

---

### Post by toby5 on 2014-05-30
> **oldfred said:**
> Instructions for installing include turning off Intel SRT before installing. :)

Also have to turn off Windows fast boot or always on hibernation or you may have major issues. And often better to have secure boot off but not absolutely required. Grub menu may not let you boot Windows with secure boot on, but you can boot both Ubuntu & Windows from UEFI menu.

See if in UEFI/BIOS you can turn off Intel SRT.
Post link to BootInfo report from Boot-Repair.
What system & video do you have.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)

SRT is the same for all vendors.
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

More info on UEFI install with screen shots in first links and Ultrabooks in the link in my signature.

Disabled the RST and the screen has disappaeared! Still having the problem where it isn't allowing me to select Windows 8 as my booting OS from the GRUB menu!

---

### Post by oldfred on 2014-05-30
You are missing a boot file for Windows. The BCD.

You probably had the boot partition on the SSD, with BIOS it is a 100MB boot hidden NTFS partition, so it would boot faster.
Grub2's os-prober looks for both the bootmgr and /boot/BCD to know which is the boot partition for Windows. Those files also can be in the main (c: drive) partition and just boot from it. Windows has the boot partition so you can encrypt the main install and the boot partition has the repair console, so you must make a repair CD or flash drive as soon as you can boot Windows if you did not do that yet. And without it it can be a bit to create the BCD. You have a BCD in your Compaq recovery, but just booting into that may reset partitions and cause issues.

I would also reinstall a Windows boot loader into the Windows drive and leave grub boot loader in the Linux drive. Then from BIOS or one time boot key you can boot either system directly if needed.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
If you have a Windows repair disk.
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If not some of the third party repair tools will recreate or fix the BCD.
      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by toby5 on 2014-05-30
> **oldfred said:**
> You are missing a boot file for Windows. The BCD.

You probably had the boot partition on the SSD, with BIOS it is a 100MB boot hidden NTFS partition, so it would boot faster.
Grub2's os-prober looks for both the bootmgr and /boot/BCD to know which is the boot partition for Windows. Those files also can be in the main (c: drive) partition and just boot from it. Windows has the boot partition so you can encrypt the main install and the boot partition has the repair console, so you must make a repair CD or flash drive as soon as you can boot Windows if you did not do that yet. And without it it can be a bit to create the BCD. You have a BCD in your Compaq recovery, but just booting into that may reset partitions and cause issues.

I would also reinstall a Windows boot loader into the Windows drive and leave grub boot loader in the Linux drive. Then from BIOS or one time boot key you can boot either system directly if needed.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
If you have a Windows repair disk.
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If not some of the third party repair tools will recreate or fix the BCD.
      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

That's a great help. I'll try booting from my Windows 8 disk and will comment back with updates! Will I lose any of the files I had on Windows?

---

### Post by oldfred on 2014-05-30
You should be able to do the repairs without destroying data.
But you always should have backups. 
Users make errors, systems make errors and hardware fails. Only if none of your data is important should you not have a backup.

Windows has been know to rewrite partition tables leaving out the Linux formatted partitions as it does not see them. And Ubuntu's auto install when used to reinstall on one drive deletes entire drive. Again did I mention backups?

---

