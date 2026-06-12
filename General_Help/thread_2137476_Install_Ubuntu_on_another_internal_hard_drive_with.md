---
title: "Install Ubuntu on another internal hard drive with boot loader on usb?"
date: 2013-04-20
forum: General Help
---

### Post by 12padams on 2013-04-20
Lets just say a computer had 3 internal harddrives:

c: 500 gigabyte ntfs drive for windows 7 (boots automatically when computer is turned on)
d: 2 terabyte ntfs drive for general stuff like backup, games, movies, music ect...
g: 1 terabyte drive unformated ready for use.

Lets just say I wanted to install ubuntu on the G drive so I have a full nice and fast Ubuntu installation without any problems of partitioning my main windows 7 drive which could corrupt files. Now I want my computer to boot normallly when I use it day to day and I don't want grub to pop up all the time and currupt the windows 7 boot loader. So can I install the boot loader on the usb so it only boots an alternative os (e.g. ubuntu) instead of windows when the usb is plugged in on boot? 

Extented Question: 
Could I install 5 different distros such as arch, ubuntu, fedora, debian and slackware as well as DOS 6.22 and windows 3.11 and windows 95 and 98 and xp on the G drive with about 9 100 gig partitions each storing an os and setup a boot loader on a usb to only boot those os's if the usb is plugged in? Would this many multiboots be possible with the grub boot loader? Would installing any of these operating systems mess up the windows 7 boot loader on the c drive?

Let's just say I love having fun with a variety of software and operating systems but I don't like having them as virtual machines  ;)

---

### Post by Irihapeti on 2013-04-20
I've often booted from an external drive.

You can play with the BIOS settings so that your external drive is the first boot device when it's plugged in. At least, I'm assuming this is possible; being lazy, I just choose which drive I want from the BIOS boot menu if I want something different from the default.

When you boot from a different drive, that drive's bootloader takes precedence. When you run "update-grub" on your external drive, it will set up an entry for Windows 7 but you can ignore it. All that does is pass control back to the Windows drive if you choose to boot into Windows 7 from the external drive grub menu. It doesn't write to the Windows drive.

Just take care when you install grub that you install it to the correct drive. It's very easy to make a mistake if you aren't careful (been there, done that).

As for the number of partitions/OSs you can have, I'll let someone else answer that.

---

### Post by ttoilleb on 2013-04-20
First, refer to this thread - [http://ubuntuforums.org/showthread.php?t=1363034](http://ubuntuforums.org/showthread.php?t=1363034)

As for the comments in it about Grub2.  They are relevant.  Grub2 works from the Master Boot Record.  It has problems with a Partition Boot Record.  That is, Grub2 is larger than a PBR, hence the reference to blocklists.  I have not played with them, so I am not sure how they work..  The issue does not exists with the MS opsys's.  (FYI: the post refers to another post that discusses DOS 6.22, win3.11, 95, 98 and XP as well as linux distros.

I am doing this on one system that includes Ubuntu 10.04.  I got around the problem by replacing Grub2 with Grub1 in U10.04.

In short, if your system will allow you to boot from a USB pen/flash drive, then it should be possible.  You would put the "main" grub as describe in the link and it would chainload to the bootloader in the partition/opsys of your choice.

HTH

---

### Post by 12padams on 2013-04-20
> **Irihapeti said:**
> I've often booted from an external drive.
When you boot from a different drive, that drive's bootloader takes precedence. When you run "update-grub" on your external drive, it will set up an entry for Windows 7 but you can ignore it. All that does is pass control back to the Windows drive if you choose to boot into Windows 7 from the external drive grub menu. It doesn't write to the Windows drive.
I already have Ubuntu on an external drive... that's not what I want. I want it on another internal drive because its too slow on an external drive. I just want it installed on an internal drive without messing up my windows 7 boot loader... that's why I mentioned having the bootloader on the usb pointing the internal harddrive

---

### Post by Irihapeti on 2013-04-20
> **12padams said:**
> I already have Ubuntu on an external drive... that's not what I want. I want it on another internal drive because its too slow on an external drive. I just want it installed on an internal drive without messing up my windows 7 boot loader... that's why I mentioned having the bootloader on the usb pointing the internal harddrive

Sorry, I misunderstood (or read too quickly).

I've never tried that, but I can't see any reason why it shouldn't work.

---

### Post by fantab on 2013-04-21
> **12padams said:**
> Lets just say a computer had 3 internal harddrives:

c: 500 gigabyte ntfs drive for windows 7 (boots automatically when computer is turned on)
d: 2 terabyte ntfs drive for general stuff like backup, games, movies, music ect...
g: 1 terabyte drive unformated ready for use.

Lets just say I wanted to install ubuntu on the G drive so I have a full nice and fast Ubuntu installation without any problems of partitioning my main windows 7 drive which could corrupt files. Now I want my computer to boot normallly when I use it day to day and I don't want grub to pop up all the time and currupt the windows 7 boot loader. So can I install the boot loader on the usb so it only boots an alternative os (e.g. ubuntu) instead of windows when the usb is plugged in on boot? 

Extented Question: 
Could I install 5 different distros such as arch, ubuntu, fedora, debian and slackware as well as DOS 6.22 and windows 3.11 and windows 95 and 98 and xp on the G drive with about 9 100 gig partitions each storing an os and setup a boot loader on a usb to only boot those os's if the usb is plugged in? Would this many multiboots be possible with the grub boot loader? Would installing any of these operating systems mess up the windows 7 boot loader on the c drive?

Let's just say I love having fun with a variety of software and operating systems but I don't like having them as virtual machines  ;)

Yes. You can install Ubuntu on the third internal HDD (lets call it **/dev/sdc**, linux does not number its drives as c:, d: or g: it will number them as /dev/sda, /dev/sdb and so on). You will install Ubuntu on /dev/sdc along with Grub, Boot-loader. After that you must change the HDD BOOT ORDER in your BIOS to boot /dev/sdc first. So the HDD with Ubuntu will boot first with Grub. Grub Menu will find all the OS on your machine and will let you pick whichever you want to boot. This will keep your Windows untouched.

Yes. You can install any number of OS. And it is possible to keep the boot loader on USB. However it may cause issues if your machine changes the usb drive number to something else than what it was during boot loader install. 

My suggestion:

Boot from HDD only, avoid Boot-loader on USB. What you can do is, for Linux Distros make 15-20GB partitions and install only as "/". And ONE Grub, say from Ubuntu will manage all OS on the System. You can have a common DATA partition that you can share between different Linux.

If you intend to install 'older' Windows on the HDD too then remember Windows will NOT give you an option "where would you like to install Boot-Loader?" SO windows will install its boot loader on the first HDD, in your understanding, on c: only and not on g: as you want to. Also Windows versions earlier than Windows7 will only boot if they are installed on c: So it is not probable that you can boot older Windows flawlessly from any other partition than c:

I hope I've been clear.

---

### Post by C.S.Cameron on 2013-04-21
Start install as normal.
When you get to partitioning select "Something else".
Select the drive and partition you wish to install to.
From the drop down select the location you wish the boot loader installed.
Complete install.

---

### Post by oldfred on 2013-04-21
You can have more than one Windows, but with multiple drives have to be careful that Windows only installs to the drive you want. We have seen Windows 7 installed on sdb, but a small boot partition on sda. I think part of the solution with newer Windows is set BIOS to boot sdc first. Not sure about older, may be safer to disconnect sda.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Windows has to boot from primary partitions. But XP can with some effort be booted from a logical with Lilo boot loader, but Windows boot loader only looks at primary partitions.

Old link has a reference where I suggested forcing grub into PBR. I would not suggest that now. That was before I really understood how you can easily use grub2 to directly boot most installs. (I had used grub legacy similar to the link on 145 installs and chainloading).  You can also have another grub boot loader on sdb even though that is a data drive. I have different versions of grub in all 4 of my drives and I always put grub in every flash drive and add my own grub.cfg which I have to manually maintain, but I do have it set to boot some installs on my hard drive.

I would keep Ubuntu's grub2 as the primary boot loader. Its os-prober will find just about any other install & let you boot it. But you may have to edit 40_custom with some of the various installs.

If you just want grub on a flash drive. You do have to add your own grub.cfg


 How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

---

