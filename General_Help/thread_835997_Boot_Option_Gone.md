---
title: "Boot Option Gone"
date: 2008-06-21
forum: General Help
---

### Post by victorash on 2008-06-21
I finaly thought I had Ubuntu 8.04 worked out. It runs from the CD no problem. So when I had Ubuntu open I click on the install icon and it went through and installed the program. When it was finished I rebooted but there was no Boot option it just loads straight into windows.

I tried to install Ubuntu again but when it came to the stage of setting up the partiton on the disk I could see that a Ubuntu was on the disk.

The boot screen just dosent come up , like I say it restarts and goes traight into windows...

Any Help Any Ideas

Thanks

---

### Post by VMC on 2008-06-21
> **victorash said:**
> I finaly thought I had Ubuntu 8.04 worked out. It runs from the CD no problem. So when I had Ubuntu open I click on the install icon and it went through and installed the program. When it was finished I rebooted but there was no Boot option it just loads straight into windows.

I tried to install Ubuntu again but when it came to the stage of setting up the partiton on the disk I could see that a Ubuntu was on the disk.

The boot screen just dosent come up , like I say it restarts and goes traight into windows...

Any Help Any Ideas

Thanks

Boot back up using livecd, then output these

```
sudo fdisk -l
cat /boot/grub/menu.lst

```

Make sure you cat out the menu.lst from the hard drive /boot not cdrom

---

### Post by danwood76 on 2008-06-21
To use the second command you will need to mount the drive first somewhere and dump the menu.lst in the mount point.
Cant tell you how to mount till we see your sudo fdisk -l first.

---

### Post by victorash on 2008-06-21
> **VMC said:**
> Boot back up using livecd, then output these

```
sudo fdisk -l
cat /boot/grub/menu.lst

```

Make sure you cat out the menu.lst from the hard drive /boot not cdrom
Sorry Im new to this, I know how to Boot up useing the live CD.
 its the "output these" bit I dont understand, How do I put that code in ?

 Thanks

---

### Post by danwood76 on 2008-06-21
If you choose 'Applications' at the Top, then 'Accessories' select 'Terminal'.
THis will bring up a command line window in whcih you can enter the commands.

---

### Post by victorash on 2008-06-22
> **danwood76 said:**
> If you choose 'Applications' at the Top, then 'Accessories' select 'Terminal'.
THis will bring up a command line window in whcih you can enter the commands.


The install process Gets through to step 7 and tells me its creating ext file sysytem, tells me to restart computer, Ubuntu screen comes up tells me to remove any disks and press any key to continue, loads up and reboots straight into windows, windows runs a checking file system on C check with a message that one of your disks needs to be checked for consistancy. Windows loads up , Message : System Settings changed, Windows has finished installing new devices , The software that supports your devices requires that you restart your computer. So I restart Windows boots up and loads as normal.

 When I check  Acronis Disk Director it shows that on my 2nd Disk (Hardrive) which is my local C drive 2 extra Partitions have been created they are: 

Ext 3 file partition with a 58.62GB capacity with 54.72Gb free space

The other partition is a Linux Swap Partition with a capacity of 2.536 Gb.

So they are on my system !


I used the live Cd to boot into Ubuntu  went into terminal this is what comes up :

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudu fdisk -1
bash: sudu: command not found
ubuntu@ubuntu:~$

---

### Post by Oldsoldier2003 on 2008-06-22
> **victorash said:**
> 

ubuntu@ubuntu:~$ sudu fdisk -1
bash: sudu: command not found
ubuntu@ubuntu:~$
sudo not sudu

also make sure you are typing an "el" not a "one" for the fdisk command

---

### Post by victorash on 2008-06-22
> **Oldsoldier2003 said:**
> sudo not sudu

also make sure you are typing an "el" not a "one" for the fdisk command



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb06cb06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       30401   244195999+   7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x219d805c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12039    96703236    7  HPFS/NTFS
/dev/sdb2           12040       20023    64131480    5  Extended
/dev/sdb5           12040       19692    61472691   83  Linux
/dev/sdb6           19693       20023     2658726   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

thanks

---

### Post by louieb on 2008-06-22
is one drive ide and the other a sata drive?  That combination leads to GRUB install confusion. The installer tries to guess which drive boots 1st. In your case it guessed wrong. Just have to fix grub. Take a look at this thread and see if it helps you get it to dual boot. 
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")
and a good description of menu.lst.
[GrubHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GrubHowto#head-1296ce2b184032373f19ad50a91d506eb886ac5f")

---

### Post by victorash on 2008-06-24
> **louieb said:**
> is one drive ide and the other a sata drive?  That combination leads to GRUB install confusion. The installer tries to guess which drive boots 1st. In your case it guessed wrong. Just have to fix grub. Take a look at this thread and see if it helps you get it to dual boot. 
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")
and a good description of menu.lst.
[GrubHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GrubHowto#head-1296ce2b184032373f19ad50a91d506eb886ac5f")

Thanks for the help, buy I think I will give this a miss and try again in a few weeks, I have managed to install Ubuntu on an older Computer with Windows XP Home that has only one drive , I used the same procedure, it installed and works great from the Dual boot option memu.

BUT This Computer:

Windows XP Professional
intel(R) Core (TM)2 CPU
6400 @ 2.13Ghz
2.14 GHZ, 3.62 GB of Ram

Processors
2x Intel(R) Core(TM)2 CPU 6400@2.13GHZ

Is a pain to set up Dual boot and I wish I had only one drive, wouldnt have  such a hassle.


Appreciate the Help !

 It runs happy from the Live CD !

Cheers

---

### Post by danwood76 on 2008-06-24
Its probably to do with your boot order and the menu.lst config
Set the boot device to be your first hard disk and then reinstall grub, it should then be able to set the correct drive priorities and so on.

Although if you've already stuck it on another machine ignore me :)

---

