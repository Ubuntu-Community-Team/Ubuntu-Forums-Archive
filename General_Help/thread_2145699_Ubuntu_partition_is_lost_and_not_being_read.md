---
title: "Ubuntu partition is lost and not being read"
date: 2013-05-16
forum: General Help
---

### Post by veebee04 on 2013-05-16
Hi,
My problem is such.
A PC in my office was set to dual boot with windows XP and Ubuntu. Now someone upgraded the windows XP to 7 and now Ubuntu has disappeared from the initial OS menus choice. I don't know what has happened to it. Moreover in windows the partition dedicated to ubuntu is shown as unformatted. Now I have some very critical files on the ubuntu partition which I desperately need. So i removed the hard disk and mounted it to a system with Ubuntu on it. However even on that system the ubuntu partition is not visible. So my query is this:
1) Is there a method to restore Ubuntu in the initial OS choices menu and boot into it so I can retrieve my files?
2) If not, what is the best way to recover the lost files on Ubuntu from the hard disk.
I am extremely proficient in the windows environment but absolutely raw with Ubuntu , so I am capable of implementing any DIY solutions as long as they are well explained. Thanks in advance

---

### Post by Irihapeti on 2013-05-16
When Windows was upgraded, Grub was overwritten with the Windows bootloader. Replacing Grub by using the Boot Repair disk should solve the problem, provided no other damage was done.

There are instructions on using the Boot Repair disk here: [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) You'll need to download it first and burn it to a CD/DVD. Don't just copy the ISO file to the disk or it won't work.

It's quite normal for Windows to see a Linux partition as unformatted, so that in itself doesn't mean there's a problem.

---

### Post by Impavidus on 2013-05-16
If you connect the disk to an Ubuntu machine and the Linux partition still doesn't show up, the partition table was damaged. You're in for some file recovery. I don't know much about that, but I think your best bet is testdisk.

---

### Post by veebee04 on 2013-05-18
> **Irihapeti said:**
> When Windows was upgraded, Grub was overwritten with the Windows bootloader. Replacing Grub by using the Boot Repair disk should solve the problem, provided no other damage was done.

There are instructions on using the Boot Repair disk here: [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) You'll need to download it first and burn it to a CD/DVD. Don't just copy the ISO file to the disk or it won't work.

It's quite normal for Windows to see a Linux partition as unformatted, so that in itself doesn't mean there's a problem.

I did that  - got the Linux disk and ran boot repair but it only restored the initial boot menu which only shows windows 7. And besides in the boot repair advanced options the two Grub tabs are disabled. So What should i do now? I got this url for seeking further help: ubuntu.com/5676145


Thanks

---

### Post by Irihapeti on 2013-05-18
Sorry, this is beyond my experience. Someone with a bit more knowledge of booting issues needs to look at it.

---

