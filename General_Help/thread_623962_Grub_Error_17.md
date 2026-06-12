---
title: "Grub Error 17"
date: 2007-11-26
forum: General Help
---

### Post by Chinfrim on 2007-11-26
Okay, this is my story,

I work on a Vista Machine, and thanks to college, I had to Install Ubuntu here, for programming uses.

So, I tried burning a CD but it woulnt start well, so I had a Real Ubuntu Liv CD come over.

Then, I installed Ubuntu 7.10, and wanted it to take 10gigs of my second HDisk.

But, Ubuntu got Greedy, and instead took away 50 gigs extra, and those 10gigs I wanted him to take, he chose to take some files I had already in that file, making those 10gigs I wanted look like 5.

I got angry at this, but since I didn-t need the space I kept it as it was.

But, then, I needed more space, and found out I had 4 partitions, those lost 50gigs were in ext3 type partition and was the fourth, It was in ext3 type.

So I thought, I-ll format it to nfts with the Live CD and merge with the VistaOS or the Ubuntu Partition, I did it, and happy with myself I rebooted, only to find the Error 17 Popping up!

I know I screwed and that I shoulnt had gone widly for formatting, now I can-t access vista or my old ubuntu, I-m typing this using the live CD!

What is need to be done? Delete the ubuntu partitions and try using the Vista recovery Cd or.. I can save this without loosing my old Vista Data? Some tons of work projects for college lost..

---

### Post by TidusBlade on 2007-11-26
I would firstly suggest you back up everything important if possible, I dont know if you can read from your Vista partition using Live CD...
Then you can try [this](http://ubuntuforums.org/showthread.php?t=442945) thread, might solve your problem :)

---

### Post by Chinfrim on 2007-11-26
Hmm.. I-ll go look at it later tonight! thatnks for the help!

---

### Post by ubuntokun on 2007-11-26
grub allows both vista and ubuntu to successfully boot. Basically when you install ubuntu it deletes vista's bOotloader and uses ubuntu . I AM ALMOST CERTAIN THAT AT A POINT IT ASKED YOU IF YOUN WANTED TO USE GRUB AS YOUR MASTERBOOTLOADER AND I ASSUME YOU CLICKED YES. Well nothing is wrong with that becuz windows will boot using grub its just that you went ahead and formated it nfts . i cant really help cauz im no computer wiz but just letting you now what grub does i thought might have helped.
Sorry but im sure sumone else has the perfect solution  to your problem.

---

### Post by TidusBlade on 2007-11-26
I remmeber reinstalling XP and it wiped my GRUB, without even asking or anything, it will probably go when installing any Windows, after linux.

---

### Post by meierfra on 2007-11-26
Open a terminal (Applications->Accessories->Terminal) and type

> sudo fdisk -l
("l" is a lowercase L)

Copy the output and post it here.

---

### Post by Chinfrim on 2007-11-27
Things evolved,

I formatted my computer using with my ASUS recovery disk and drivers,

It went smoothyl, but Grub still fails..

Error 22.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
129 heads, 4 sectors/track, 454344 cylinders
Units = cylinders of 516 * 512 = 264192 bytes
Disk identifier: 0x0ab90a2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4       27787     7168000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *       27787      283720    66030592    7  HPFS/NTFS
/dev/sda3          283720      454339    44019712    f  W95 Ext'd (LBA)
/dev/sda5          283724      454339    44018688    7  HPFS/NTFS

It-s what I get running that command, what now?

---

### Post by meierfra on 2007-11-27
You did succeed to erase Ubuntu. But you still need to restore the MBR. Check out this link:

[http://ubuntuforums.org/showthread.php?t=616540#2]("http://ubuntuforums.org/showthread.php?t=616540#2")

---

### Post by Chinfrim on 2007-11-27
> **meierfra said:**
> You did succeed to erase Ubuntu. But you still need to restore the MBR. Check out this link:

[http://ubuntuforums.org/showthread.php?t=616540#2]("http://ubuntuforums.org/showthread.php?t=616540#2")

ok, trying it with my ASUS RECOVERY Cd, Which only Reformated.. no recovery option.

waiting for it to load... 

It only has 3 Options.. Recover WIndows to First Partition ONly,

Recover Windows to Entire HD

Recover Windows to Entire HD with 2 Partition.

No Code Lines, nothing.

---

### Post by meierfra on 2007-11-27
If you have the ubuntu LIVE CD, try the third method. Otherwise get Supergrub.

---

### Post by Chinfrim on 2007-11-27
Okay, will try in some minutes.

---

### Post by Chinfrim on 2007-11-27
> **meierfra said:**
> If you have the ubuntu LIVE CD, try the third method. Otherwise get Supergrub.

To I need to be connected to the internet? After doing sudo apt-get update I had tons of "Failed"

and sudo apt-get install ms-sys failed because the ms-sys wasn't found.

---

### Post by meierfra on 2007-11-27
> Do I need to be connected to the internet? 

Yes, both "apt-get update" and "apt-get install" require internet connection.

---

### Post by Chinfrim on 2007-11-27
> **Chinfrim said:**
> To I need to be connected to the internet? After doing sudo apt-get update I had tons of "Failed"

and sudo apt-get install ms-sys failed because the ms-sys wasn't found.

Yeeees! Vista is back! Now for the instalation!

Thanks a LOT.. now I only need to reduce the ubuntu partition on my oldie comp.. but I know the deal now!

---

### Post by meierfra on 2007-11-27
Good!  Let the people in thread [Grub Error 17]("http://ubuntuforums.org/showthread.php?t=442945") know about your progress.

---

### Post by athomson on 2007-11-27
Hi,

It appears that you just need to restore the Master Boot Record [MBR] so that Windows will boot again.  Really four choices, 1) use a Windows Install disk in recover-mode and manually fix it [which does not appear to be an option for you], 2) Get Free DOS and use it to restore the MBR, or 3) Take the MBR from another Windows system, 4) Re-install Ubuntu.

Read these carefully before doing anything.  If at all possible backup up your entire disk or your Windows partitions.  

_Option 2: Free Dos_

Free Dos Boot Cdrom image (this is about 7.1 MB in size) and use it to fix the master boot record [MBR].  

[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso)

Write this down on a piece of paper :-)

```

Press Enter
Type 2 (for safe mode)
cd FREEDOS
FDISK /MBR

```

Reboot and run the command you just wrote down.

_Option 3: Other PC MBR_

If you have another PC that has Windows on it, you could copy part of the MBR from it and use it to restore yours.  This involves booting from the Ubuntu install cdrom, opening a terminal, copying the MBR to a file, copying the file to a floppy [or USB], then rebooting your PC with Ubuntu, opening a terminal, saving your MBR to a floppy or USB stick, and then restoring the MBR.  This does not always work, but when it does, its fast.

Note: You do not want the whole MBR. Why? Because the whole MBR contains the partition table, and the other PC partition table may not be the same as yours. The commands below only grab the boot portion of the MBR and ignore the partition table [which is what you want].  See here for a good explanation of this: 

[http://www.freesoftwaremagazine.com/articles/issue_20_tips_and_tricks?page=0%2C3](http://www.freesoftwaremagazine.com/articles/issue_20_tips_and_tricks?page=0%2C3)

_Instructions for Other PC MBR_

Boot Ubuntu on other PC

Open a terminal
```
Application->Accessories->Terminal
```

Become root
```
sudo -i
```

Grab the boot portion of the MBR
```
dd if=/dev/hda of=boot_mbr.img bs=446 count=1
```

Copy it to a floppy or usb stick. 

Boot Ubuntu on your PC

Open a terminal
```
Application->Accessories->Terminal
```

Become root
```
sudo -i
```

Back up your MBR, you want all of it so get 512 bytes
```
dd if=/dev/hda of=my_mbr.img bs=512 count=1
```

Save it to the floppy or USB

Copy the other PC's mbr file to /tmp

Restore the boot portion
```
dd if=/tmp/boot_mbr.img of=/dev/hda bs=446 count=1
```

Reboot.  It should come up in your Windows boot loader.

_Option 4: Re-Install Ubuntu_

There is a 4th option, and this is to reinstall Ubuntu back to PC using the partition that it originally had. This will restore grub and then you can boot to Windows and use it to change the MBR.  

---

Andy

---

### Post by athomson on 2007-11-27
Great!

I was too slow in typing my instructions.

Andy

---

