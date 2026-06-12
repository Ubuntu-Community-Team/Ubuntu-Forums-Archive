---
title: "If this problem isn't fixed I cannot use Ubuntu at all!!"
date: 2007-01-28
forum: General Help
---

### Post by presbp on 2007-01-28
I have my 300GB external harddrive partitioned into 4 partitions. 1st is 15gb for Ubuntu, 2nd is 270MB for linux-swap, 3rd is 15GB FAT32 and the 4th is NTFS and takes up the remaining space on the drive which is 255GB> I didn't want to use the entire drive for Ubuntu so I partitioned it this way. If I install Ubuntu first then format the FAT32 and NTFS partitions (formatting in Windows) then when I try to boot Ubuntu I get

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

So I formatted the external drive, partitioned it out then went and formatted the Windows partitions first. After they were formatted I installed Ubuntu and Voila! Ubuntu would work. Now the problem continues... I was in Ubuntu and copied some files to the FAT32 partiton so I could take them over to Windows. Then I booted down went into Windows and copied the files, then booted down, rebooted and tried to boot Ubuntu, then I got the same error again. Why cannot I use these partitions without bothering Ubuntu??

---

### Post by r4ik on 2007-01-28
The solution seems to be in this thread,

[http://www.ubuntuforums.org/showthread.php?t=279884](http://www.ubuntuforums.org/showthread.php?t=279884)

I cannot confirm but the people involved are more than capable.

Good luck !

---

### Post by soze on 2007-01-29
I don't have any insight into your specific problem, but I would say that keeping the swap partition on an external drive is a bad idea.

---

### Post by strabes on 2007-01-29
Windows likes to be installed first, on the first partition (sda1 or hda1)

---

### Post by presbp on 2007-01-30
I got everything working correctly this is awesome.

---

### Post by writeson on 2007-02-17
How did you get it fixed, I have the same problem. Can't get Ubuntu 6.10 installed from the CD, either for the Desktop or Server. This is a new system, SATA driver (though I'm not sure if the CD drive is SATA or IDE).
Thanks in advance,
Doug

---

