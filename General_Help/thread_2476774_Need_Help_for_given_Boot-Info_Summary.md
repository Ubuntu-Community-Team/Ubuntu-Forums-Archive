---
title: "Need Help for given Boot-Info Summary"
date: 2022-07-06
forum: General Help
---

### Post by ankit.mishra on 2022-07-06
Hello All,

Please find below link of our Ubuntu Boot info Summary

[https://paste.ubuntu.com/p/5t264zx92r/](https://paste.ubuntu.com/p/5t264zx92r/)

Please do let us know the next set of steps to take.

---

### Post by sudodus on 2022-07-06
Please describe the history of your operating system: When and how was it installed? Did it work before? Please try to describe what happened before you reached the current problem.

This kind of description is as important as the data in the boot-info summary.

---

### Post by ankit.mishra on 2022-07-07
New Ubuntu 20.04 was installed sometime in the year 2020.
Yes it was working well until 3 weeks back.
We were using this system as a staging environment for our internal applications.
The system was not reachable from a different machine within the same LAN.
When the System was physically access, there were more than 250 update pending.
One of our developer tried update command "sudo apt update" when he got readonly file system error. Screen-shot of the same can be found in the attachment.
We rebooted the system presuming that the error may go away on reboot.
On system restart Busybox Initramfs error showed up.
We followed the instruction given in the link below.
[https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/](https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/)
On trying the above solution, system booted normally. On reboot system went back to same Busybox Initramfs error. This happen twice.
9. There after the system went into GRUB shell[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290695&stc=1[/IMG]

---

### Post by oldfred on 2022-07-08
I cannot read the screen shot, too small for my old eyes.
Please either post terminal output in code tags or post to pastebin.
Easy to add code tags with Forum's Go Advanced editor and # icon.

You show this:
> This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).
Be sure to always boot in UEFI boot mode.

But your system is UEFI and has a UEFI install. 
And you seem to have issues mounting sda1.
I might first try fsck on sda1, and/or check disk for issues with smartmontools.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)

---

