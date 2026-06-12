---
title: "after grub,windows isnt running"
date: 2015-01-04
forum: General Help
---

### Post by salary on 2015-01-04
Hi, i deleted my windows 8 in Toshiba and i established windows 7-64 bit and Ubuntu 14.10-64 bit.my bios preferences csm mode because it stopped in uefi mode.when i come grub screen,i see ubuntu and windows but i can run ubuntu although i can not windows.if i select windows,grub's purple screen is covering all the screen.There is also windows's starting sound but screen is purple.i used boot repair but its output "...The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from  the start of the disk. Your BIOS may not detect them. You may want to  retry after creating a /boot partition (EXT4, >200MB, start of the  disk). This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair]....". Also,in the gparted,windows disc partition has exclamation mark in the red circle and it says "Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3"

---

### Post by ajgreeny on 2015-01-04
See Boot-Repair in my signature and run the Boot-info script from that.

Do not at this stage accept the automatic boot repair option; just post the pastebin link you are given back here for the report made by the script.

---

### Post by salary on 2015-01-04
[http://paste.ubuntu.com/9670589/](http://paste.ubuntu.com/9670589/)

---

### Post by ajgreeny on 2015-01-04
OK, it looks to me as if you should be safe to run the recommended boot-repair and get everything running as it should be.  I did wonder if you had a mix of MBR and UEFI but everything is running in a legacy MBR manner.

I admit that I do not have windows any more except an install of XP in VirtualBox merely to update my satnav, so I am now a long way out practice at dealing with dual boot situations, so you may wish to wait for other replies before carrying out the repair.
Forum member **oldfred** is the guru in these matters and hopefully he may pass by and help you more than I can.

---

### Post by oldfred on 2015-01-04
System looks normal for  a BIOS configuration.

The far from start of drive is an issue that only applies to some older BIOS. I have not seen a system, yet with UEFI that needed that separate /boot. And my old systems from 2006 & 2009 did not need it.

Boot-Repair cannot fix most Windows issues. You can try f8, just at the same time you press the Windows entry in grub, but grub to Windows is usually too fast for that to work. You may have to use Boot-Repair to temporarily install the Windows boot loader to use f8 to get into Windows Repairs or uses your Windows 7 installer to get into repairs. Best to always have a Windows repair CD or flash drive, just like you have your Ubuntu live installer, so you can make repairs if needed.

 f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

        "Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

---

### Post by Impavidus on 2015-01-04
If you hear Windows's startup sound, then Windows starts. It just doesn't show anything on the screen, suggesting some kind of graphics driver problem, which I don't know about. The exclamation mark in gparted shows that there is probably file system damage in the Windows partition.

---

