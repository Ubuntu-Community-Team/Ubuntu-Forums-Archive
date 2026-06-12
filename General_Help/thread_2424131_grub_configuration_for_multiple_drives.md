---
title: "grub configuration for multiple drives"
date: 2019-08-04
forum: General Help
---

### Post by dictum99 on 2019-08-04
My machine has 3 bootable drives, one Ubuntu 19.04 and other two are Win10-1903. It is an UEFI machine.

I want to move away from using BCDEDIT and instead make the Ubuntu drive the first one to boot in the BIOS / boot options.

I want to configure grub on that Ubuntu drive, what would the syntax look like for chaining these two drives?

---

### Post by yancek on 2019-08-04
Have you tried running sudo update-grub while booted into Ubuntu, with all 3 drives attached?  Also, while booted into Ubuntu, runn the following command and post the output here:  sudo efibootmgr
If all 3 systems are EFI installs,  do you have one EFI partition on one drive or separate EFI partitions on each drive?

---

### Post by oldfred on 2019-08-04
What brand/model system. Some make it more difficult than others.
Have you updated UEFI from vendor. Many with HP says that improves the ability to boot Ubuntu.

Do not run any autofixes, be sure to boot Ubuntu live installer in UEFI boot mode.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dictum99 on 2019-08-05
The machine is MSI Titan GT80 SLI.

It has 4 SSDs in it, #3 is where Ubuntu is at and #1 and #2 are both Windows. I can move the Linux drive to the #1 in BIOS boot order and then 

I've used Windows BCDEDIT command to create multiboot and it works very well - with Windows. It does not see a Linux disk at all with a letter assigned to it making it impossible to add it to my configuration. Meaning my best bet is not BCDEDIT but Grub.

Each OS is on its own separate disk.

---

### Post by oldfred on 2019-08-05
All they all UEFI or all the old BIOS boot mode?
Specs show RAID 0, which causes issues for grub install, but can be worked around. Or did you reinstall so using each SSD separately?

Really need Boot-Repair report to see configuration.

Often issues common by brand, so these models may have similar issues?
       MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[URL="http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72"]http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72
      [/URL]
 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815) 
    [URL="http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72"]
[/URL]

---

### Post by yancek on 2019-08-05
>  It does not see a Linux disk at all with a letter assigned to it making it impossible to add it to my configuration

Windows booting in UEFI is very limited and won't boot Linux or some other windows systems, explained at the link below so Grub is probably the best solution.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

Windows does not assign drive letters to Linux partitions, as far as I know, never has.  Generally you will only see the existence of a Linux partition in windows in something like Disk Management unless you install some 3rd party software so that is standard behavior.  Best run boot repair and post the info requested above to get some help.

---

