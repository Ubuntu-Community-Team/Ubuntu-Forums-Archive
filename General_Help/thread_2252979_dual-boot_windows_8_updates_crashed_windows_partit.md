---
title: "dual-boot windows 8 updates crashed windows partition - Boot Info to read"
date: 2014-11-16
forum: General Help
---

### Post by maxpesa on 2014-11-16
Hello everyone, I installed Kubuntu in dual-boot with Windows 8 (not 8.1) a weeek ago and both ran properly, I was aware of the possibility of crash caused by Windows updates when in this config, and I was likely to set my Windows partition to not auto-update, but, fascinated by my new OS, I  used Windows only yesterday, and... Update! Win partition crashed after the auto-reboot, with the Lenovo logo and the 6 balls spinning endlessly. 
I tried to use Boot-Repair but it did not solve my problem.
> An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/9044826/](http://paste.ubuntu.com/9044826/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
I don't know how to read these logs, and I kindly ask someone to read it and tell me something. I also didn't understand the last paragraph, sorry. :(

I have a Windows image Backup in case, and a Win Rscue CD. It ran but I was not certain of its possible "reaction" to the presence of GRUB. is it likely to create problems to my boot settings? I heard it is likely to erase everything on my HD

THINGS THAT MAY BE IMPORTANT:
- Boot-Repair is set to "Secure boot" (ticked under "Advanced options"), but my UEFI/BIOS isn't

---

### Post by yancek on 2014-11-16
I don't know what your windows update did but, if you look at the info from the script it shows sda2 as an EFI partition.  In a proper installation, you will see the names of the windows efi files as well as the Ubuntu efi files.  There are none.  sda4 shows as windows 8 but also shows there is a boot.ini file there.  I don't use windows much but, it is my understanding that file has not been used since xp?  It shows your grub.cfg menu file on sda6 which looks like a separate boot partition but the system installed on sda8.  If you have an EFI partition you should not need a separate boot partition.  If your windows 8 was pre-installed then it was probably UEFI and if Kubuntu worked it probably was also.  I don't have experience with UEFI so hopefully someone will come along with suggestions on how you can repair these problems.

---

### Post by maxpesa on 2014-11-16
Yes, my system in currently set to work with EFI.
Yes, the presence of boot.ini is suspicious, it has been deleted since windows xp.
Yes, I have a separate GRUB partition, the video I followed told me it's better to have a separate partition to install the bootloader.

---

### Post by oldfred on 2014-11-16
I do not know what video you saw but separte /boot partition is not required for most desktop installs. Full drive LVM or encryption or other server type install may need a separate /boot. Otherwise it just adds complications and additional effort to repair and maintenance of old kernels is more important. Supposed that is now fixed but you still need to check that /boot does not get full.

Script says it installed grub and found Windows efi boot file, so I think for some reason script is not now showing files in the efi partition?

And any Windows maintenance will automatically reset it to be the default in UEFI menu. You have to go into UEFI and reset Ubuntu to be first.
Some of the newest Windows seems to always reset itself to first.
And some vendors modify UEFI to only boot the UEFI entry with Windows, but will boot hard drive so work arounds for those systems HP & Sony, maybe others are available.

Grub will not currently boot Windows with secure boot on. If you really want secure boot, you have to use UEFI menu or one time boot key to choose which system to boot.

---

