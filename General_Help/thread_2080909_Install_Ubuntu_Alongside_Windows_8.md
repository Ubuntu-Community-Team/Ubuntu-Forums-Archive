---
title: "Install Ubuntu Alongside Windows 8"
date: 2012-11-05
forum: General Help
---

### Post by CrusaderAD on 2012-11-05
I'm running into an issue with an Acer Aspire S7. When I boot to the Ubuntu usb drive and go to install Ubuntu, it doesn't give me the option to "Install Alongside Windows". It just asks to erase everything and install or "something else". Something else shows about 10 different partitions, most ntfs. Does anyone know if it's possible to install alongside windows given these circumstances?

---

### Post by CrusaderAD on 2012-11-05
Update, I've attempted a Wubi installation and it doesn't work. So I ruled that one out. It couldn't find the /ubuntu/winboot/wubildr.mbr file despite me having used bcdedit to point it in the right direction.

---

### Post by Mark Phelps on 2012-11-05
If you're using MBR disk, the max partitions you can have is four Primary or 4 Primary+1 Extended.  IF you have either max, the installer will not let you create anymore partitions.

BEFORE you try to force anything, be advised that using the slider to shrink Win7/Win8 partitions risks corrupting them. Instead, you need to use the Win8 Disk Management utility to shrink the Win8 partition down to make room for Ubuntu -- but leave the unallocated space as is, do not format it.

Then, when you boot into Ubuntu, you use "something else" to format the unallocated space and do the install.

However ... if you're using UEFI disk, I don't know how to format those, sorry.

---

### Post by CrusaderAD on 2012-11-05
Thanks for the info. I know it's currently using the UEFI method to boot. So resizing the partitions and installing Ubuntu shouldn't matter right?

Also, how does one reinstall windows 8? On pre-installed machines, there is no CD Key on the machine anymore and there's no reinstallation disk. Do they expect you to make a backup USB or something and restore instead of reinstall?

---

### Post by CrusaderAD on 2012-11-05
I decided to just install Ubuntu as my main system and not bother with a dual boot. Now when I boot up after a successful install, it says no bootable device found. What happened?

---

### Post by SimonErich on 2012-11-14
Hi guys,

did you find a solution for the problem CrusaderAD.
I'm actually running into the same thing here.

Just got my Acer Aspire S7 and tried to install Ubuntu with something else alongside Ubuntu.

I shrinked the Windows parition with the Windows part tool and created a new ext4 and swap partition.
I installed everything and now I can't boot into a system anymore because I always get the "no bootable device" messsage.

I think it has something to do with the Raid0 ssds in the aspire s7. They put 2 128gb ssds in there in a raid0 and this is why we see all those paritions.

Does anyone know how to install it on this or has an idea. Right now I can't even access Windows.

thanks

best regards
   Simon

---

### Post by oldfred on 2012-11-14
Usually with any RAID Ubuntu will not install as gparted nor the installers partitioning tools work with RAID.

I think these were Windows 7 but may be similar. 

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

Did you use 64 bit version and install in UEFI mode? UEFI menu should give two options to boot install CD or USB, one UEFI and the other BIOS/legacy/AHCI etc.

If installed in BIOS mode that can cause issues, but Boot-Repair can convert a BIOS install to UEFI. But best to post BootInfo report to see details first.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by SimonErich on 2012-11-14
Hello Oldfred,

thank you for your answer.

I tried the repair tool and it didn't work. Still the same "no bootable..." message. After finishing the repair process it even said that GRUB was still not found.

Here is the link: [http://paste.ubuntu.com/1358824/](http://paste.ubuntu.com/1358824/)

I think one of the bigger problems is that I destroyed my raid0 partitioning table by just changing the paritions in the ubuntu installler.
I read that gparted supports raids with an additional programm, that is istalled in ubuntu 12.10.
When I start gparted now i always get error messages that there was an error and it crashes.

How can i repair it ? Will it work if I let Ubuntu use the whole parition instead of "something else"?
I will still need to find a way to reinstall windows from the backup drive, but to make it easable until then.

thanks
 Simon

---

### Post by oldfred on 2012-11-14
It looks like you still have efi install in RAID. 

All the /dev/mapper/isw_dfjifdigfe_HDD0 are the RAID drive & partitions. 

I really do not know RAID, so I do not know if drivers were missing or script could find some partition tables. RAID itself looks normal from what little I do know.

Are you booting from UEFI menu or have you tried f12 or whatever key is a one time boot key?

---

### Post by SimonErich on 2012-11-14
Hello,

I actually installed it in UEFI mode (at least that's what I saw in the BIOS afterwards).

But I also changed it to BIOS Legacy now - still get a "no bootable device".
I also tried it with F12 and selecting the Harddrive.

The only thing that works is booting with the Ubuntu Live USB Stick.

Does anyone have an idea how to get my windows up and running again and setup Ubuntu next to it? :)

Thanks
  Simon

---

### Post by oldfred on 2012-11-14
If Windows is in UEFI mode you have to have Ubuntu in UEFI mode. 
Or you have to reinstall Windows in BIOS/MBR which I do not believe is possible with your version.

Because none of the was Windows 8 with UEFI, I did not post it. But it may give some clues.

Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by SimonErich on 2012-11-16
Hi oldfred,

thank you for your reply.

I did read your Links and go through them and the fastest solution seemed to be whiping the whole ssd and recreating partitions without the raid0.

I just disabled the Raid (changed to normal bios and then hit CTRL + I to get to the Intel Raid Menu). Then I deleted all partitions on the harddrive and installed Ubuntu.

It is working now, but I need to find a way to get a windows for my second partition.

I actually don't mind that I now have 2 ssds (one for linux, one for windows). Is there any other advantage in having a raid0 other than making it seem like one big ssd?

simon

---

### Post by oldfred on 2012-11-16
Do you have two SSD?

Most of the Intel SRT seem to be a hard drive with a SSD as cache to speed booting and some tasks. Not sure why or how they use RAID to implement that but it seems to be consistent across vendors with sizes of drives being the only variable.

You can check drive read speeds with hdparm. My SSD is an OEM low cost. Newer ones I have seen posted were twice as fast.

SSD speed
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec

---

### Post by SimonErich on 2012-11-16
Hi

yes the Acer Aspire S7 has two 128GB SSDs built in.
They are actually always being listed as one of the fastest ssds out there and in every aer aspire s7 review they praise them.

Here is a review with benchmarks:
[http://www.notebookcheck.net/Review-Acer-Aspire-S7-391-Ultrabook.83561.0.html]("http://www.notebookcheck.net/Review-Acer-Aspire-S7-391-Ultrabook.83561.0.html")


```
simonerich@simonerich:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads: 1168 MB in  3.00 seconds = 388.95 MB/sec
simonerich@simonerich:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads: 1218 MB in  3.00 seconds = 405.59 MB/sec

```

It would be interesting to see if the raid boosts the performance or not.

---

### Post by oldfred on 2012-11-16
I am not a particular fan of RAID on desktops. It used to be with those compiling lots of applications they wanted RAID for speed. But RAID is mostly used for servers where many users are all using it at the same time. Some think it is for backup but that is not the case as anything you delete is gone. So backups are still important.

I got my SSD as a boot drive. I did not find I could type any faster and my Internet does not download any faster. :) 
But it does boot noticeably faster and some larger applications seem to load a bit faster the first time, but RAM caches recent activity so reuse is not any quicker.

---

### Post by CrusaderAD on 2012-11-17
> **SimonErich said:**
> Hi oldfred,

thank you for your reply.

I did read your Links and go through them and the fastest solution seemed to be whiping the whole ssd and recreating partitions without the raid0.

I just disabled the Raid (changed to normal bios and then hit CTRL + I to get to the Intel Raid Menu). Then I deleted all partitions on the harddrive and installed Ubuntu.

It is working now, but I need to find a way to get a windows for my second partition.

I actually don't mind that I now have 2 ssds (one for linux, one for windows). Is there any other advantage in having a raid0 other than making it seem like one big ssd?

simon

Here's what I did... I enabled Legacy in the BIOS, THEN installed Windows 8 as normal, then installed Ubuntu 12.10 afterwards alongside Windows 8. Now the Ubuntu Grub shows up and lets you pick which OS to go into. Worked for me.

---

### Post by SimonErich on 2012-12-22
Hi guys,

just wanted to let you know my solution. It is kind of similiar to CrusaderADs but I managed to install it in UEFI.

I had to reorder the Windows 8 DVDs from Acer (had to call an expensive hotline to get them - but I finally got them).

After receiving them I removed the Intel Raid0 (as I don't need them and I read that installing Ubuntu would be complicated) by pressing STRG + I during the boot process (in Legacy BIOS mode).

I then used an Ubuntu live USB to recreate GPT Partitiontables on both HDDs with "gdisk".

Then I switched back to UEFI mode and installed Windows 8 from the Acer disks (I used the first variant - restore Windows on one SSD).

After that I installed Ubuntu via the LiveCD on the second hard drive.
(I let Ubuntu partition the second drive 

Everything seemed fine, but the system always booted Windows and ignored the Ubuntu ssd. I searched for two days and tried every solution I've found, but couldn't find a working solution (reinstalling grub, modifying grub, installing grub on sda1, ...).
I was about to give up and install it in Legacy mode when I thought I should give the "boot repair" live cd a try.

I used the live CD and ticked the "rename windows boot file" (or something like that) checkbox, because it seems Acers uefi boot options include searching for this file and they ignore other settings.

After that everything worked fine and now I'm running a Windows 8 + Ubuntu 12.10 UEFI boot without a problem.

---

