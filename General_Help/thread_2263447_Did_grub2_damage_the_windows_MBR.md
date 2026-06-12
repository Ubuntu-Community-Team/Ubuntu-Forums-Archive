---
title: "Did grub2 damage the windows MBR ?"
date: 2015-02-01
forum: General Help
---

### Post by oygle on 2015-02-01
Have been using Kubuntu 14.04 for quite a while now. Needed to add a windows XP pro hard drive, and followed the instructions at [How to have a custom GRUB2 menu that is maintenance free]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen"). That all seemed to go fine, however after modifying some files and updating with [grub2]("http://ubuntuforums.org/showthread.php?t=2076205&p=13219643#post13219643") , upon the next boot into windows xp, it simply kept rebooting.:confused:

When booting into safe mode, it stopped at some drivers, and then rebooted again. If grub2 has damaged the MBR of the win xp hard drive, how do I recover from that please ?

Ran bootinfo script, and it seems the MBR of the win xp hard drive is okay, see [here]("http://paste.ubuntu.com/9991831/")

---

### Post by oldfred on 2015-02-01
If from BIOS you directly select the Windows drive to boot does it work? I would think it does as then BIOS reports sdb as the first drive and rdisk in boot.ini says drive 0.

I am not sure I still fully understand Windows in any drive but the first.

BIOS writes drive info to hard drive. And Boot drive in BIOS is in grub always hd0. Not sure with Windows but it usually expects to be the first drive. Your boot.ini shows it as the first drive, line 494 shows rdisk(0). 

But grub does a drivemap command that switches the drive order so when booting Windows it thinks it is first. That seems to work ok when you boot sdb with grub and then the drivemap  makes sda be hd0 and the Windows in sda works. 

Not sure if you need to remove drive map, and/ or edit boot.ini to be rdisk(1) or both.
If you use a Linux editor on boot.ini be sure to save in Windows mode. Gedit will default to Linux but now has a Windows save mode. 

 If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

---

### Post by oygle on 2015-02-01
Thanks oldfred. I have since learned that one cannot simply take a windows xp pro hard drive from one computer, place it into another computer, and expect it to "work". Have tried setting the boot order at BIOS and same problem. However now I believe the problem is only a windows one and not a grub problem. Interestingly, the hdd that has xp on it has the 'boot' flag set for dev/sdb1 and the drive that has Kubuntu on it also has the boot flag set. Grub seems to be handling the swapping of boot drives okay though. Thanks.

---

### Post by yancek on 2015-02-01
The boot flag is irrelevant to any Linux installation.  You don't need it at all, only windows.

---

### Post by oygle on 2015-02-01
Okay thanks. Have got the Win xp drive to boot up okay. It was totally a windows problem; had to do a re-install with the original CD. No, grub _did not_ damage the Windows MBR.

---

