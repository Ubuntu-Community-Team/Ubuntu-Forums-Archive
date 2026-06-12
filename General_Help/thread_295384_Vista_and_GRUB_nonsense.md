---
title: "Vista and GRUB nonsense"
date: 2006-11-08
forum: General Help
---

### Post by lonelypauly on 2006-11-08
i have a system with 2 seperate SATA hard drives.  one drive has kubuntu 6.6   and the other has XP. ive run a dual boot setup for nearly a year with no problems...however, tonite i decided to backup and wipe out what little i had on the XP drive and install vista.  well guess what? lol...GRUB wont load and i cant access my kubuntu drive anymore. I get the following message: "Error loading operating system" windows WILL load after setting the drive to boot in bios...but no such luck with kubuntu. i tried unplugging the xp/vista drive and i still get a boot load error.  Vista melted down after the I loaded the Nvidia drivers haha, so i reinstalled XP.

how can i access my kubuntu drive...as that is my main OS...please help.

---

### Post by TheLoneMan on 2006-11-08
Vista installs overwrite GRUB. This question has been asked and answered several times, a future way to prevent repeating questions, and perhaps the quickest way to finds a solution to this problem, is to search the forums for threads pertaining to your situation.

Cheers.

---

### Post by lonelypauly on 2006-11-08
actually i wasnt able to find a case specific to mine, and haven't been able to fix the problem yet.  i unplugged the windows drive and still cant figure out why my ubuntu drive wont boot.  what the is best way to get this drive to boot? please help.  grazie.

---

### Post by DaveBorealis on 2006-11-08
Hello,

This link should sort out the mess for you.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Best regards,
Dave

---

### Post by glotz on 2006-11-08
Microsoft *wants* to get you screwed. Not a nice company.

See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lonelypauly on 2006-11-08
thanks for the link....but no such luck...i followed the instructions very carefully but im still having the same problem...here is the message im getting at boot:

> root (hd1,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sdb1 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...

---

### Post by glotz on 2006-11-08
What did you exactly do?

---

### Post by lonelypauly on 2006-11-08
i just followed the instructions at the link posted on this thread...now im seeing:

**EXT3-fs: journal inode is deleted.**


i am totally lost here...i ran the install setup just like the instructions say but it seems that my hd is not mounted when i check the status in the manual partitioning tool.  

this is not working out so well...and i need to get to those files...i dont even care about recovering my OS as much as backing up my data.  is there an easy way to do that?

---

### Post by Hairy_Palms on 2006-12-19
to backup your data you can either do it via the live cd or if its in ext3 use the windows driver
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

