---
title: "Is it possible to run Ubuntu from external HDD?"
date: 2013-02-02
forum: General Help
---

### Post by cwblanch on 2013-02-02
Hi,[INDENT]Is it possible to run Ubuntu, or any other Linux, from an  external HDD?
I've tried looking it up once or twice, but haven't come up with anything that looked promising or it was really old posts on other forums.

I guess it would work to partition the external with an ext4 partition...but I just don't know enough to continue and I don't want to lose all my data.


Thanks
[/INDENT]

---

### Post by oldfred on 2013-02-02
You have to use Something else or manual install. The main reason is that is the only install method that gives you the choice on where to install the grub2 boot loader and you want that on the external drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

     
With manual install you have to specify partitions yourself. One suggestion wtih some options.
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
    
       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by cwblanch on 2013-02-03
...I'll have to work on, and mess around with this for a while. :lolflag:
I'm still new to messing with booting and sizing procedures.

Will doing this erase my whole external? Or just the parts I specify to change formats?

---

### Post by oldfred on 2013-02-03
It depends on how you install. If you say to use entire drive it erases everything. You can shrink an existing partition and install to unallocated if you want auto install, but then grub will be written to sda.
With manual install you can shrink & create partitions at will. But I prefer to do that with gparted first, just so the partition changes are not part of the install. It may be because years ago it was more difficult to do partitions are part of the install.

---

### Post by cwblanch on 2013-02-24
> **oldfred said:**
> It depends on how you install. If you say to use entire drive it erases everything. You can shrink an existing partition and install to unallocated if you want auto install, but then grub will be written to sda.
With manual install you can shrink & create partitions at will. But I prefer to do that with gparted first, just so the partition changes are not part of the install. It may be because years ago it was more difficult to do partitions are part of the install.


Is this process the same when having an OS run from a usb drive?
To be clear, I don't mean just installing it to the computer through the usb drive, I mean installing it to the usb drive to run from there...or is that even possible?

---

### Post by Bashing-om on 2013-02-24
cwblanch; Hi !
> 
To be clear, I don't mean just installing it to the computer through the  usb drive, I mean installing it to the usb drive to run from there...or  is that even possible?     Here is one guide:
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
And even more supporting info:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
another way:
[http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/)
[INDENT]my regards

[/INDENT]

---

### Post by oldfred on 2013-02-24
Do you want the live version that is also an installer or a full version just like you install to the hard drive.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by cwblanch on 2013-03-04
> **oldfred said:**
> Do you want the live version that is also an installer or a full version just like you install to the hard drive.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

A full version would be awesome. Something that can be ran from the usb drive

---

### Post by oldfred on 2013-03-05
A full version to a flash drive is just like any install to a second drive, with just a few settings for flash drive to reduce writes. I have full install in 8GB / (root) with a 8GB data partition on a 16GB flash drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

      
 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

Since flash & USB ports are a bit slower than hard drive a lightweight version may be a bit faster.

 HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

