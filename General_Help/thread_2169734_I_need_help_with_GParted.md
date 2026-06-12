---
title: "I need help with GParted"
date: 2013-08-23
forum: General Help
---

### Post by peter1897 on 2013-08-23
I want to extend my first partition dev/sda2 and add to it the unallocated space of 17.62GB that is in the extended partition. But if i select dev/sda2 and choose move/resize it doesn't recognize the free space next to it. Is it possible to add this unallocated space to my first partition, and if yes, how to do this?

---

### Post by Bucky Ball on 2013-08-23
Not possible. You are effectively attempting to resize one partition over another. The extended partition is a holder and is that size, whether there's anything in it or not. 

sda2 is a primary partition. sda1 is an extended partition. Both partitions, regardless of whether they're empty or not.

Shrink the extended partition to leave free space in front of it then expand sda1 into the free space. Done.

In other words, drag the beginning of sda2 up to the beginning of sda5 then the end of sda1 to the beginning of sda2.

---

### Post by peter1897 on 2013-08-23
It doesn't allow me to do what you are sugesting. I can't drag sda/sd2 in any direction.



[ATTACH=CONFIG]245639[/ATTACH]

---

### Post by oldfred on 2013-08-23
You have to move extended which is sda1 first and use check to process that change to in effect move the unallocated outside of the extended partition. Then as a totally separate step you can expand sda2.

---

### Post by peter1897 on 2013-08-23
How to move the extended partition? If i select dev/sd1 the option for resize/move is not available.

[ATTACH=CONFIG]245640[/ATTACH]

---

### Post by peter1897 on 2013-08-23
I get it done. I had to turn swap off to unlock the drive and then resize the extended partition.

I have another problem. For some reason i suddenly cannot install Windows XP anymore. I am trying to install it from USB and after restarting it loads the boot menu to the stage when it says "Launching setup from (hd1,0)" and stops there, only show a black screen.
I am not sure but i think this is a problem with the boot sector. I want to completely wipe out the boot sector and then installing Grub. How can i do this?

---

### Post by oldfred on 2013-08-23
You need the partition formatted with NTFS but also need the boot flag. You were showing boot flag on sda4. If you want to install to sda2, you need to use gparted and manage flags and move boot flag to sda2. Make sure you only have one boot flag per hard drive.

---

### Post by peter1897 on 2013-08-24
These are my current partitions. On dec/sda1 i installed Windows 7 and on dev/sda4 i want to install Windows XP.

[ATTACH=CONFIG]245656[/ATTACH]

I had Windows XP installed on dev/sda4 but suddenly i started getting message that hal.dll is missing on boot, and even so i copy the file hal.dll from the Windows XP installation files it couldn't load the operating system even in safe mode. So i deleted the partition and tried to reinstall Windows XP but now it doesn't want to install it.

I don't think the problem is with the partitions because the install hangs on "Setup is inspecting your computer's hardware configuration" and then show just black screen. I have reinstalled Windows XP many times on my laptop, this is happening for the first time. And if i am able to install Windows 7 why it doesn't want to install Windows XP. 

I think it is a problem with the boot sector on my hard disk but i am not sure.

---

### Post by oldfred on 2013-08-24
The error on hal.dll missing is almost always a mis-configured boot.ini. When you installed it should be correct. But post boot.ini, it should be referring to drive 0 and partition 4.

Ignore any reference to grub legacy as that is obsolete.
 Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

---

### Post by peter1897 on 2013-08-24
I had problem with hal.dll file before deciding to reinstall Windows XP, now i just can't install XP. Windows XP was installed on dev/sda4 but i deleted the partition and reformat it with GParted and now if i try to install XP it just hang at "Setup is inspecting your computer's hardware configuration"

I used Super Fdisk from live CD and it gave me some partition table error which is saying something like: "No any right partition table on hardisk".

I can boot Ubuntu, and Windows 7 which i have also installed, and yesterday i installed Windows 7. Only Windows XP i can't install any more. 

This is my boot configuration report from Boot Repair:

[http://paste.ubuntu.com/6022132/](http://paste.ubuntu.com/6022132/)

---

### Post by oldfred on 2013-08-24
You show boot flag on sda1 or Windows 7. Did you want to overwrite that as XP installs to partition with the boot flag?

---

### Post by peter1897 on 2013-08-25
Currently the boot flag is on sda1 with Windows 7 install. But i have tried with boot flag set on sd4 and it still doesn't want to install XP. I don't think the boot flag is the problem at all, because i have installed Windows XP recently on partitions with no boot flag set on them.
Something else is preventing the XP install.

---

