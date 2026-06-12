---
title: "[SOLVED] GRUB1.5 Error 17"
date: 2008-06-15
forum: General Help
---

### Post by jon64 on 2008-06-15
This is my situation, every time i boot up my linux machine it halts at the grub bootloader. I receive an error 17 right after the "GRUB Loading stage1.5."

Before this happened i was dual booting with Windows server 2003 and ubuntu and it was working fine. Then i wanted to try out Kubuntu to see how it was like and right after i rebooted the computer i received the error 17 message. 

So after i received the message i ran the live cd and typed sfdisk -l and this is wat came up:
root@ubuntu:/home/ubuntu# sfdisk -l

Disk /dev/sda: 91201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

Device Boot Start End #cyls #blocks Id System
/dev/sda1 * 0+ 89698 89699- 720507186 83 Linux
/dev/sda2 89699 91200 1502 12064815 5 Extended
/dev/sda3 0 - 0 0 0 Empty
/dev/sda4 0 - 0 0 0 Empty
/dev/sda5 89699+ 91200 1502- 12064783+ 82 Linux swap / Solaris

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

Device Boot Start End #cyls #blocks Id System
/dev/sdb1 * 0+ 38911 38912- 312560608+ 7 HPFS/NTFS
/dev/sdb2 0 - 0 0 0 Empty
/dev/sdb3 0 - 0 0 0 Empty
/dev/sdb4 0 - 0 0 0 Empty


I can still get to my Windows Server 2003 OS but i want to get my ubuntu OS back or at least get files that i need from the ubuntu hard disk from my Windows Server 2003 hard disk.

I just tried using the Live CD to run "sudo grub" and "find /boot/grub/stage1" and when i typed in find /boot/grub/stage1 i received "Error 15: File not found"

I don't know what to try anymore =/ please help!

---

### Post by logos34 on 2008-06-15
Did you perhaps tell it NOT to install grub when you installed Kubuntu over ubuntu?  

Probably the fastest way to fix this would be to reinstall kubuntu.

---

### Post by Sef on 2008-06-15
> Device Boot Start End #cyls #blocks Id System
/dev/sda1 * 0+ 89698 89699- 720507186 83 Linux


Device Boot Start End #cyls #blocks Id System
/dev/sdb1 * 0+ 38911 38912- 312560608+ 7 HPFS/NTFS

I think I see the problem.  Only one boot should be set, not two.  Windows needs to be on the first partition and should be the one that the boot is set for.

To remove the boot on Kubuntu, either use a *buntu Live CD and go into the partition manager or download [GParted]("http://gparted.sourceforge.net/") and remove the boot flag on Kubuntu.

---

### Post by logos34 on 2008-06-15
> **Sef said:**
> Only one boot should be set, not two.

I thought that only applied when you have two flags on the *same* drive.

What gets me is that stage1 is nowhere to be found:

> **jon64 said:**
> I just tried using the Live CD to run "sudo grub" and "find /boot/grub/stage1" and when i typed in find /boot/grub/stage1 i received "Error 15: File not found"

---

### Post by jon64 on 2008-06-15
Sorry about the double post :( 

Im in Gpart right now on a ubuntu 8.04 LIVE CD and i just finished removing the boot flag off of the linux partition. One thing that i saw that was strange was while in gpart the linux partitions filesystem is unknown and when i right click the partition and go to information under "Status:" it says Not mounted. I dont know if this means anything but i thought id report it to you guys :)

---

### Post by jon64 on 2008-06-15
Okay i switched the primary HD to the windows partition and Im not getting the dual boot menu instead it boots straight to windows server 2003.

If there isnt any way i can get GRUB back is there a way i can transfer files from my linux partition to my Windows partition? I'm not even sure if i can even transfer files from my linux partition over to my windows partition since in GPART in linux didnt even recognize its own partition... :(

---

### Post by drs305 on 2008-06-15
Here's a link to a thread that begins:
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

I don't know if your MBR was affected but you can read it for yourself.

---

### Post by logos34 on 2008-06-15
> **jon64 said:**
> One thing that i saw that was strange was while in gpart the linux partitions filesystem is unknown 

maybe running a filesystem check from the livecd will clear it up. 

[B]sudo fsck /dev/sda1
[/B]
Either that or use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to straighten out the partition table.

---

### Post by logos34 on 2008-06-15
> **jon64 said:**
> is there a way i can transfer files from my linux partition to my Windows partition?

if all else fails, yes, you can get [fs-driver ]("http://www.fs-driver.org/")for windows side, in order to read/copy linux files.  But like you say there may be problems.

ADD: did I understand you correctly about installing kubuntu over ubuntu root?

---

### Post by jon64 on 2008-06-15
> **logos34 said:**
> if all else fails, yes, you can get [fs-driver ]("http://www.fs-driver.org/")for windows side, in order to read/copy linux files.  But like you say there may be problems.

ADD: did I understand you correctly about installing kubuntu over ubuntu root?

To be honest im not really sure lol, im pretty new to the linux os but i have enough knowledge to work with it, its just this time im out of my league lol but i ran sudo apt-get install kubuntu-desktop i believe and when i restarted it ran really strangely with lots of weird glitches so i decided to restart again to see if that fixed my problem and that was when i started to get the ERROR 17 error.

---

### Post by jon64 on 2008-06-15
> **logos34 said:**
> maybe running a filesystem check from the livecd will clear it up. 

[B]sudo fsck /dev/sda1
[/B]
Either that or use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to straighten out the partition table.

Omg i love you so much in a non homo way! sudo fsck /dev/sda1 fixed it! im loading into kubuntu right now and its fixing the hard disk! ill be able to have my files and all my apts i set up! WOOOOOOOOOOOOOOO :popcorn: Lets just hope nothing else happens while in the proccess of fixing the partition :D 

thanks everyone! :) CHEERS!

---

### Post by logos34 on 2008-06-16
ok, glad it's working.

Enjoy kubuntu!

---

