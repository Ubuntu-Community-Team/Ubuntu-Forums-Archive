---
title: "Windows 10 update wiped grub and ubuntu 12.04 dual boot."
date: 2016-04-14
forum: General Help
---

### Post by robcowdrey-t on 2016-04-14
Dear all. Apologies for the long post. 

I have had an Acer notebook for several years now, originally shipped with Win7, to which I added Ubuntu as a dual boot environment (If I recall via Wubi), and after numerous updates ended up at Ubuntu 12.04, which has all worked just fine. It's a BIOS machine, not UEFI.

Given the lack of issues down the years, I went ahead and updated to Windows 10 (again without issue) and so when the latest Win10 (1511) update came along, it didn't concern me. How wrong could I be.

During the Win 10 update the notebook rebooted as expected, but the came back with an 'error: no such partition. grub rescue' prompt. Other people have run into this, and so far this is what I have tried;

I made a boot rescue USB stick (14.04), and found a way to run boot-repair.  This completed ok, and allowed the Win 10 update to finish, and Windows 10 runs fine again.  However boot repair didn't bring back the grub / dual boot option menu. Instead it just boots straight into Win10 each time. I have read of people using Testdisk but I couldn't seem to get this to run using the command line (I don't think its in Synaptic for 14.04 ?) so am now stuck.

I think boot-repair does show my old Ubuntu partition (as sda4), but I'm at a loss as to how to fix the mbr and get grub back ? Any help really appreciated, thank you. 

Output of boot-repair; [http://paste.ubuntu.com/15824871/](http://paste.ubuntu.com/15824871/)

---

### Post by Impavidus on 2016-04-14
That doesn't look like a wubi install, which is good, as wubi is no longer supported.

The Windows update deleted the Ubuntu partition, which was a logical partition inside sda4, left of sda5. This seems a common problem with Win10. When the Ubuntu partition is gone, grub cannot find its configuration files and is unable to do any more than giving a rescue shell.

The Ubuntu partition was just deleted, probably not overwritten. So the data is still recoverable. I've never needed data recovery myself, but this may help: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by robcowdrey-t on 2016-04-14
Thanks for the reply. 

I really wanted to see if there is a way to resolve the MBR / grub issue to get it back (if possible? ) and data recovery would be a last resort. Essentially I have around 95 gigs on sda4 as 'unknown' at this point - though that's exactly where my 12.04 resides. 

Possibly Testdisk would be able to do this - but as I posted before I'm not sure it's still available or working for 14.04. Everything else works just fine from the USB stick, so I should be able to access any necessary repository.

I'm guessing this Win10 update will catch a few people out in the Ubuntu community.

---

### Post by grahammechanical on 2016-04-14
> I'm guessing this Win10 update will catch a few people out in the Ubuntu community.

It already has. There are posts on this forum about it. The advice I have seen, although I have not studied it in detail, is to use TestDisk to fix the partition table. And there is a version 7 of TestDisk that was released 18th April 2015. 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Regards.

---

### Post by yancek on 2016-04-14
As indicated above, your partition table was re-written by windows and did not include the Ubuntu partition.  If you look at the output from fdisk in the code block below, you can see that from the beginning of the Extended partition (        120,068,094 ) to the beginning of the swap partition (         311,015,424 ) there is a lot of room.  That's where your Ubuntu was/is so try  testdisk to fix the partition table.

> /dev/sda4         120,068,094   312,580,095   192,512,002   5 Extended
/dev/sda5         311,015,424   312,580,095     1,564,672  82 Linux swap / Solaris

---

### Post by oldfred on 2016-04-14
Both testdisk & parted rescue can restore missing partition. 
But a few have clicked on wrong thing and lost added partitions.
Best to make backup of current(incorrect) partition table just in case, so you could start over if necessary. Most recovery partition, a few can then boot, but others had to reinstall grub.

 backup before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt
So you know sectors (you already have this in Summary Report):
sudo parted /dev/sda unit s print

      
 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by Wizy on 2016-04-14
Unfortunately it happens like that sometimes. See i came across how to fix windows 10 issues with Ubuntu [http://www.wizytechs.com/2015/07/worried-about-windows-10-automatic.html](http://www.wizytechs.com/2015/07/worried-about-windows-10-automatic.html)

It might be of help here

---

### Post by robcowdrey-t on 2016-04-14
Thanks to all for the replies.

I have got Testdisk 7.0 to run and it has found the 'hidden' partitions and updated the disk. So I can now see my old files as a 96Gb volume via the 14.04 USB copy of Ubuntu. Great ! It sees 3 x HPFS partitions, the first bootable and 2 as Primary. There are 4 more partitions, all Linux and these are listed as 'L' for Logical.

So do I just cut my losses and copy off the docs and pictures to an external drive - or is there a way to re-build grub to give the mbr / boot up menu ?

I will freely admit I was on the edge of my understanding as regards the terminology in Testdisk. There is an entry in the front end menu to 'Write MBR code - Write TestDisk MBR code to first sector'. Does anyone know if this will return the boot menu option - or something else ?

---

### Post by Impavidus on 2016-04-14
Copying your files to an external drive is always a good idea. Hard drives do break down sometimes, best to have backups at all times.

I never used Testdisk, so I don't know the specifics. But if it successfully restored all Linux partitions, Boot-Repair you used earlier can fix grub. It should detect Ubuntu this time and install grub instead of the generic Windows bootloader.

---

### Post by robcowdrey-t on 2016-04-14
Thanks for the boot-repair tip Impavidus - boot-repair did indeed put grub back in place and all working now as before.  The only slight change are the entry titles listed in grub, but that is a minor and I will just need to search how to edit the entry titles so they make better sense ! So in my case to fix this;

1- Via a working pc, make a bootable Ubuntu USB stick.
2- Check the boot order in BIOS on the original machine to allow the USB priority to boot. Allow a cold boot from the USB stick.
3- Connect to the net, download boot-repair and run an automatic check. After re-boot this allows the Win10 update to complete.
4- Re-boot to check Win10 boots and loads ok.
5- Shut down and re-insert Ubuntu USB. Power up.
6- Download Testdisk, extract the files and run from terminal (version 7.0 of Testdisk used in my case).
7- Allow Testdisk to analyse the disk to find the 'hidden' partitions.  Once checked and correct, allow Testdisk to write this to disk.
8- Still running from the USB stick, check that the 'missing' Ubuntu volume is now visible, in the shortcut bar.
9- Download boot-repair again and re-run to re-build grub.
10- Shutdown and restart - check that both Win10 and Ubuntu start correctly from the grub menu.

Thanks once again for all the pointers and tips. I need to learn a bit more around grub for sure !

---

### Post by grahammechanical on 2016-04-14
I am glad that TestDisk is proving to be part of the answer to this problem. I agree with the suggestion to now use Boot Repair. This is what TestDisk does when we accept the option to install MBR code.

[http://www.cgsecurity.org/wiki/Menu_MBRCode](http://www.cgsecurity.org/wiki/Menu_MBRCode)

I have no idea if doing that will load Ubuntu but if it does the commands to run are

```
sudo update-grub
sudo grub-install /dev/sda
```

If there is only one hard drive. 

Regards.

---

### Post by philinux on 2016-04-21
Just did the update with no problems. Ubuntu on an extended partition. Maybe thats why.

---

