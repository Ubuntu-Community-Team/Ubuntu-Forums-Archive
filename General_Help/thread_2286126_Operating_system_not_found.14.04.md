---
title: "Operating system not found.14.04"
date: 2015-07-10
forum: General Help
---

### Post by fred58 on 2015-07-10
I've been using Ubuntu on my hard drive for a long time and this is the first time I've gotten this problem. My laptop doesn't detect my hard drive after a couple of hard shutdowns and on rare occasions it boots Ubuntu normally. I've bought a new hard drive and changed the cmos battery but I'm still getting the operating system not found message. My laptop is a Sony vaio v505bx. Im runing ubuntu from a live cd right now.

---

### Post by dino99 on 2015-07-10
with such a case, first check that the bios/uefi find and well identify that device. Then boot with gparted live cd/usb and glance at the disk/partition(s) for possible error(s)/warning(s) (often shown with a red triangle when something is bad). Also check that the boot partition has the 'boot' flag and is formatted as ext4 or a supported linux format.
If the previous checks are normal, then consider purging the actual grub (sudo apt-get purge grub*) then reinstall it (sudo apt-get install grub-pc) and select /dev/sda to set it on.

---

### Post by fred58 on 2015-07-10
Is this a grub problem then?

---

### Post by CitadelUniversal on 2015-07-10
Usually the error you've found indicates an installation problem, do you have two hard drives in your laptop if so you may need to change the boot-loader in the BIOS setting usually by F1 or F2 though other Function keys vary depending on manufacturer. If you don't have two hard drives then you didn't install the Ubuntu OS properly please read the documentation [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by fred58 on 2015-07-10
I've been using Ubuntu on the current hard drive for a long time now so I don't think its a bad installation.

---

### Post by tgalati4 on 2015-07-10
Welcome to the forums.  How old is the laptop?  Will it boot without the battery?  Plug in the power cord, remove the battery, and see if it will boot.  A weak battery will suck up current so that the disk drive won't spin, hence "No operating system found."

---

### Post by fred58 on 2015-07-10
It boots fine from without the battery. I think the problem not detecting the hard drive has to do with grub but I'm not so sure.

---

### Post by fred58 on 2015-07-10
I did the grub purging commands and got 
0 upgraded,0newly installed, 0 to remove and not upgrade.

---

### Post by fred58 on 2015-07-10
What commands can I use to see what's wrong with the hard drive? I've used Ubuntu for a long time on my current hard drive and I'm getting a operating system not found after a couple of hard shutdowns. I bought a new hard drive and tried to install Ubuntu on that but it didn't detect any drives to install it on. I'm using an old Sony vaio pcg v505bx from 2003.

---

### Post by Bashing-om on 2015-07-10
fred58; Hello;

> **fred58 said:**
> I did the grub purging commands and got 
0 upgraded,0newly installed, 0 to remove and not upgrade.

But what you have not said; Do you now boot up ? Or do we need to delve in deeper and look at  the /etc/fstab file and /boot/grub/grub.cfg comparing the UUIDs to what 'sudo blkid' relates ??? As you advise you had changed the hard drive, unknown how you re-installed the operating system ; Perhaps the UUIDs remain from the old install ?

[INDENT][INDENT]there is that path that seems right
[INDENT][INDENT][INDENT][INDENT]but leads to ??
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2015-07-10
That's info you should add to your existing thread [http://ubuntuforums.org/showthread.php?t=2286126](http://ubuntuforums.org/showthread.php?t=2286126) not open a new one.
It's actually the most important clue. I suggest you check whether or not the HDD is actually recognized in BIOS. If not then there's no point in even attempting to install. A laptop from 2003 uses probably IDE drives and the chipset may or may not have size limitations... Please get back to your original thread, post this info and what appear on BIOS.

---

### Post by fred58 on 2015-07-10
I forgot to state that my laptop had a couple hard shutdowns. Ubuntu kept checking the hard drive for errors when booting up then it started not detecting the hard drive after that. 
The default boot order in my bios is
1 optical drive
2 floppy
3 hard drive 
4 network

I change the hard drive to the top, save, and try to boot.

i bought the new hard drive to see if my laptop detect the drive and tried to install Ubuntu on that. Right now I'm using my old hard drive but I'm running a live Ubuntu cd from the disk drive.

---

### Post by Bashing-om on 2015-07-10
fred58; OK;

All good info to know. 
Perhaps now would be a better time to look at the hard drives partitioning.
Post back the results of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
see what we have to work with and then decide on what to try and boot .
Also what releases are you running on each of the hard drives ? Release 15.04 now uses systemd as the initiate system rather than the former upstart . We do now need to know what system we are working with.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-11
Merged you second thread back to this one. Please do not post another thread on same issue.

Have you tried repairing partitions? Hard shutdowns often damage them. And remember the elephants.
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by fred58 on 2015-07-11
ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 14.04.2 LTS i386" TYPE="iso9660" 
ubuntu@ubuntu:~$

---

### Post by oldfred on 2015-07-11
That shows no hard drive at all. Just liveCD/DVD as sr0.

Does BIOS show drive?

---

### Post by fred58 on 2015-07-11
It shows the the drive option even if it's not plugged in.

---

### Post by Vladlenin5000 on 2015-07-11
> **fred58 said:**
> It shows the the drive option even if it's not plugged in.

:confused:

BIOS usually shows the drives by make/model...

---

### Post by oldfred on 2015-07-11
You should have something like this attached photo of my BIOS. It shows 3 drives & DVD.

---

### Post by fred58 on 2015-07-12
It's always had those same drives. Before the hard drive had a star next to it as the first boot option but now the star is gone since the hard shutdowns.

---

### Post by oldfred on 2015-07-12
But is drive shown specifically?

But then it seems drive is not showing any partitions now?

---

### Post by fred58 on 2015-07-13
After doing the command [COLOR=#000000]*sudo e2fsck -C0 -p -f -v /dev/sda#*[/COLOR]
I'm[COLOR=#000000] getting a no such file or directory while trying to open /dev/sda#[/COLOR]
I don't know what partition number my drive is in so I went from sda1-10.

---

### Post by oldfred on 2015-07-13
But if drive is not shown and parted -l is not showing which partition(s) are ext4 formatted then the command will not work.

Does BIOS specifically show your hard drive by model & serial number as the screen shot I posted above? If not check connections or replace cables. But it could just be drive has totally failed.

If drive is shown then try testdisk.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 [       ]("https://help.ubuntu.com/community/DataRecovery") Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

    
[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by fred58 on 2015-07-13
Photos of the bios and boot menu. I can hear the two hard drives spinning so I don't think its a bad connection.

---

### Post by oldfred on 2015-07-13
First screen says no IDE?
And second can you select the hard drive entry and then does it show anything?

---

### Post by fred58 on 2015-07-13
No I cant expand any of the options.

---

### Post by oldfred on 2015-07-13
Spinning may mean just power but not signal.
If BIOS does not correctly see drives and report those drives to operating system, no operating system can use drive.
Double check connections. 

I used to have issues with the old IDE connections where just opening case and trying to do something would loosen one of those very wide 80 conductor cable connections just enough that it looked connected but was not. But when drive did not appear I knew I had to reopen case and check connections. I soon learned not to totally close up case before rebooting and making sure everything worked.

---

