---
title: "Can't boot into Ubuntu"
date: 2018-01-23
forum: General Help
---

### Post by melody5697 on 2018-01-23
A few days ago, I was having problems on my computer. If I remember correctly, the main issue was that it was being really slow, but there were a few other issues as well. I tried to look at the system resources to see if too much RAM was being used, but then it wouldn't let me go to the tab that tells me that, so I just restarted the computer. But when I tried to boot into Ubuntu, it didn't work. Here's what it said:
```
[      0.205344] platform NSFT0101:00: failed to claim resource 1: [mem 0xfed40000
-0xfed40fff]
[      0.205349] acpi MSFT0101:00: platform device creation failed: -16
/dev/sda6 contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev/sda6: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
          (i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda6 requires a manual fsck


BusyBox v1.22.1 (Ubuntu 1:1.22.0-19ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
Sorry if there are typos. I copied that from a picture I took of the screen with my phone. I decided to boot into Windows 10 to ask about it here, but that didn't work, either. (NOW it's working. I'll explain in a moment.) I selected Setup in Grub and went to the system diagnostics thing and did a system test, and it failed the Hard Drive Short DST Check. (I don't really know what that means. I also don't understand most of the stuff it's telling me when I try to boot into Ubuntu.) After the failure ID and the Product ID, it said:
Hard Drive 1 - Primary HDD Bay*
 I decided to just give up and wait for my grandma to bring me my old computer (I recently moved out of her house and I left some things there) and then send this one in for repairs, but then she brought me my OLD old computer (which has a completely broken hard drive and a defective RTC battery and couldn't boot from live CDs or USBs for some distros). So I decided to try to boot this computer one last time before installing Linux on a flash drive. I still couldn't boot into Ubuntu, but when I tried to boot into Windows 10, it said it was repairing the hard drive (or something like that). Now I can boot into Windows 10, but I still can't boot into Ubuntu. Now, I'm aware that this is a hardware issue, not a software issue. But I just thought that since Windows 10 is working (it's really slow, but it's working), maybe it's also possible to get Ubuntu to work. Is there anything I can do to get it to work? I have Ubuntu 17.10 installed. Here's the Amazon listing for the laptop because the specs are listed there: [https://www.amazon.com/gp/product/B01M7VW4M9/ref=oh_aui_detailpage_o08_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B01M7VW4M9/ref=oh_aui_detailpage_o08_s00?ie=UTF8&psc=1)
I sure have terrible luck with computers, phones, and tablets...

---

### Post by oldfred on 2018-01-23
It seems reboot may have run a fsck, but better to run a full file check.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by melody5697 on 2018-01-23
> **oldfred said:**
> It seems reboot may have run a fsck, but better to run a full file check.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1
I don't understand... Also, you misspelled tries.

---

### Post by oldfred on 2018-01-23
Just to make sure it is not a corrupted file system you need to run fsck (e2fsck) to see if that repairs it.

---

### Post by melody5697 on 2018-01-24
> **oldfred said:**
> Just to make sure it is not a corrupted file system you need to run fsck (e2fsck) to see if that repairs it.

Okay, so I've said yes to all the repairs it asked to make, but then it said:
```
Error reading block 101189833 (Input/output error) while getting next inode from scan. Ignore error<y>?
```

I said yes, figuring I could go back and fix it if I needed to. But then it asked if I want to force rewrite. I don't understand what it's asking to rewrite. Should I say yes?

---

### Post by melody5697 on 2018-01-24
Right before it said that there was an error reading that block, it said:
```
[  695.169116] Buffer I/O error on dev sda6, logical block 101189833, async page read
```
Just thought that might be important.

---

### Post by melody5697 on 2018-01-24
I'm tempted to just say yes and see what happens... But I have no idea what I'm doing and I don't want to risk losing any of my files.

---

### Post by melody5697 on 2018-01-24
Okay, I decided to go ahead and say yes, and the exact same thing happened with block 101189834. I guess I'll keep going and see what happens... Or maybe I should stop before I break something.

---

### Post by melody5697 on 2018-01-24
I said yes to everything and now it's working. My computer even passed that test it failed earlier. :) Good to know that my grandpa was wrong about it being a hardware issue. (He's a computer programmer who has used Linux but prefers OS X.) I wonder what caused the problem in the first place. Maybe it was because I had to use the actual physical power button to shut down because my computer froze. (I usually have lots of programs open while my computer is in sleep mode, and my swap partition isn't big enough. That's the last time I let the installer do the partitioning for me. It's not like I can't do it myself. I just figured it would be faster to let the installer do it.) That can damage the computer, right?

---

### Post by oldfred on 2018-01-24
Glad you got it working.

Hard shutdown or power failure when system is working can cause file corruption and then you have to run fsck.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

And always have good backups. Then you can easily reinstall system and restore your data.
       
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery

[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834) 

[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

