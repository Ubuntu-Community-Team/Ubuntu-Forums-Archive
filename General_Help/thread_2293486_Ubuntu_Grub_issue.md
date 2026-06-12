---
title: "Ubuntu Grub issue"
date: 2015-09-05
forum: General Help
---

### Post by lucas20 on 2015-09-05
I had Ubuntu on my HDD (I had it in a 3 way partition design 1 partition for backing up anything, 1 for Windows 7/10 and one for Ubuntu).

I recently removed Windows 10 and went back to Windows 7. After doing so I figured I would do away with ubuntu and clean up my partition list a bit (It was a mess on how it was arranged).

 After going to ubuntu and using gparted to move all Un-used/Free space to the same block, I removed ubuntu and used Windows 7 repair disk to fix boot. 

A few days later, I'm now stuck at:
'Error: Unknown Filesystem
Entering rescue mode...'

I can't boot to CD, USB, HDD, etc.
Everything has the same outcome.
My current Partition/HDD list:
'(hd0) (hd0,msdos6) (hd0,msdos5)

Earlier I was having the 'Disk read error' and took out my 2nd HDD, and changed the SATA port to the first which has then brought me to this.

I'm fairly sure I completely corrupted the HDD via gparted by moving partitions around and things of that nature.

Any ideas on what to do from here?

(LiveCD's won't boot, so remember this!)

Similar Threads:
[http://ubuntuforums.org/showthread.php?t=1822023](http://ubuntuforums.org/showthread.php?t=1822023)
[http://askubuntu.com/questions/142300/fixing-grub-error-error-unknown-filesystem](http://askubuntu.com/questions/142300/fixing-grub-error-error-unknown-filesystem)

(After doing things shown here I am still stuck on grub.
I completely deleted Ubuntu & Grub itself and fixed boot then this randomly occured.
I cannot boot into anything, and doing anything replies with unknown filesystem.)

Everyone apparently fixed it via CD's and USB's, However I cannot boot into these.
My systems is currently 100% unusable.

SOLUTION:
Used another hard drive & booted a live CD that way. Used the command > sudo mkfs.ext4 /dev/sd(A/B/etc here) after that, just install another OS over it. However, since you're stuck at grub recovery you WILL need a Linux LiveCD, windows or anything else will NOT work.
It will fully format the drive, you have an unlikely chance of retrieving any data from that drive, trust me it's a pain.
Thanks to all whom have suggested things!
Lesson learned: NEVER USE GPARTED FOR WINDOWS PARTITIONS.

---

### Post by grahammechanical on 2015-09-05
Did you use Gparted to resize the Windows partition? Windows utilities for Windows partitions and Linux utilities for Linux partitions.

With Ubuntu removed and Windows 7 loading successfully for a few days then what you are seeing is a Windows 7 problem. "Disk read error" has to do with the hard disk and not the SATA port the drive is plugged into.

Not being able to load a CD or USB or even a hard disk is something to do with the settings in the BIOS boot system utility.

---

### Post by lucas20 on 2015-09-05
Yeah I resized windows partitions w/ gparted, And the only reason why I changed SATA ports was because it was a suggestion from a forum I had read, meaning take out any other drives and move SATA ports, atleast I'm past that. And I'll check BIOS for what I can find on this, have found many threads with the same exact problem, most of them turned out to be un-solved. If possible I'm completely willing to format HDD / do anything possible to get this PC back up and running.

---

### Post by lucas20 on 2015-09-05
Found nothing in BIOS, flashed CMOS to see if that would do anything, of course it didn't. Seems I'm at a standoff now.


==EDIT===
Put an Ubuntu LiveCD on a flash drive and hoped that I had some luck.
Output log:
'Remove diss or other media.
Press any key to restart'
(Pressed Enter)
'Error: Unknown FileSystem
Entering Rescue Mode...'

Flash drive is formatted to FAT32.

---

### Post by yancek on 2015-09-05
Without knowing your drive/partition info, there isn't much anyone can do but guess.  Boot any Linux Live CD and open a terminal and run the two commands below.  Use the sudo if you are using Ubuntu:

```
sudo fdisk -l
sudo parted -l
```

That's a lower case Letter L in both commands.
You indicate in your first post that you removed Ubuntu and Grub and used the windows repair disk to put the windows bootloader on the drive.  From your post, it apparently then booted windows for several days.  So how did you get to this state if you have removed Ubuntu and Grub?

You seem to be saying in your first post that you had three partitions on one drive, one a backup, one for windows and one for Ubuntu.  In a later post you mention two drives.  Do you have two drives?  .  If the (hd0) is your windows partition, it shows boot code on two logical partitions and windows needs its boot code on a primary.  When you run the commands above, make sure both drives are attached and post it here.  If that doesn't help you may need to get the boot repair software and run it then post the output of the Creat BootInfo Summary.  You will need a Linux system to do this.

---

### Post by lucas20 on 2015-09-05
> **yancek said:**
> Without knowing your drive/partition info, there isn't much anyone can do but guess.  Boot any Linux Live CD and open a terminal and run the two commands below.  Use the sudo if you are using Ubuntu:

```
sudo fdisk -l
sudo parted -l
```

That's a lower case Letter L in both commands.
You indicate in your first post that you removed Ubuntu and Grub and used the windows repair disk to put the windows bootloader on the drive.  From your post, it apparently then booted windows for several days.  So how did you get to this state if you have removed Ubuntu and Grub?

You seem to be saying in your first post that you had three partitions on one drive, one a backup, one for windows and one for Ubuntu.  In a later post you mention two drives.  Do you have two drives?  .  If the (hd0) is your windows partition, it shows boot code on two logical partitions and windows needs its boot code on a primary.  When you run the commands above, make sure both drives are attached and post it here.  If that doesn't help you may need to get the boot repair software and run it then post the output of the Creat BootInfo Summary.  You will need a Linux system to do this.

Can't boot CD's, USB's, Etc..
And I do have 2 drives, but the other one isn't in.
I have 2 partitions currently on this drive, the backup and windows which goes out as:
Hd0, Hd0 msdos6, Hd0 msdos5.
I believe one of the msdos is the recov partition as it doesn't list my backup partition.
Last time I checked partition list before having this issue it was:
/dev/sdb3
/dev/sdb5

The other drive is practically broken and is only used as storage. It can't hold any OS and such.

---

### Post by yancek on 2015-09-05
Have you tested the flash drive you created on another computer to see if it boots to eliminate that as the problem?
Inability to boot a CD/DVD/flash drive is a problem but unrelated to the system installed whether it is windows or Linux.

In your initial post, you indicate you used the windows disk to repair the bootloader.  This would limit you to booting windows.  Were you able to successfully boot windows after doing this?  If so, this really isn't a Grub/Ubuntu or Linux problem.  It might be that when you changed the partitions, you now have windows on the master boot record pointing to its boot files.  The only partitions you show on that drive are logical partitions not primary which are needed for windows boot files.

If you aren't able to get any additional info, nothing we can suggest.

---

### Post by oldfred on 2015-09-05
You said you flashed CMOS, that should reset everything back to defaults.
But defaults often are an issue. You usually have to make some changes to allow USB booting.

Is system newer UEFI or older BIOS?

---

### Post by lucas20 on 2015-09-05
1. USB boots fine on other PC's aswell as CD's.
2. Yes, I've been able to boot to windows for about 4 days until grub randomly came up after getting a 'disk read error' and started doing this.

3. I believe it's an older BIOS, it has an EFI/Non-EFI option, I've loaded fail safe and recommended bios settings and tried to boot with no luck.
Mother board is GA-78LMT-USB3

---

### Post by oldfred on 2015-09-05
I am not sure if it matters whether Intel or AMD based.
But Gigabyte all seem to need IOMMU setting changed to get USB ports to work.

 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by lucas20 on 2015-09-05
I don't see an 'IOMMU' option in my bios, however I do have these enabled.
USB Controllers
USB Legacy Function
USB Storage Function


===EDIT===
Also I do not believe that would matter, the USB can be booted as it tells me to remove disks or other media and press any key to boot/restart. Then grub comes up to tell me no again.
I'm still wondering how the hell grub came back to haunt me like this, I remembered that if I boot into my 2nd HDD it would send me to grub rescue when I've never had ubuntu installed on it. I'll do some fooling around with that and see if for any way in this un-usual process that grub is installed there.
Also at this point I think I should try to install a low end OS on that second HDD and try to fix my first as quickly as possible before it dies on me. I'll try this aswell.


===EDIT2===
Tried using other HDD, it came up with 'DISK BOOT FAILURE, PLEASE ENTER SYSTEM DISK AND PRESS ENTER'
Couldn't get past it, I'm quickly running out of options here.

---

### Post by oldfred on 2015-09-05
Without booting something either DVD or flash drive it is extremely difficult to know what to suggest.

I see from your manual that motherboard still uses IDE as default. That would have been for XP, better to use AHCI.
And better to turn on Smart Status so drives can be evaluated for problems.

When you said you refreshed BIOS was that the latest version from Gigabyte or just the version you had?

---

### Post by lucas20 on 2015-09-05
Last version from working boot is what I selected on the menu since I didn't have anything else. I'll look around for an updated BIOS though.

===EDIT===
After looking in the case a bit more I realized I didn't plug in the 4-pin molex to power the other HDD. I should be able to boot on this drive then format the other through this, hopefully it works, it's one of my best options so far.

edit#2-- Disk read error appeared once more hmm.
Fixed  by using a different SATA cable.
I got a linux LiveCD to boot!

edit#3-- Ubuntu livecd boots, then shows nothing but disk read errors, and I mean ALOT of them.
Doesn't boot all the way but it gets to there, any ideas on this?
Also, no other disk will boot other than an ubuntu livecd
Opened up Gparted and it only shows liveCD as a device.
Doesn't list my HDD's. Only lists /dev/sdr0 as a mac partition table.

---

### Post by lucas20 on 2015-09-05
Update:
Gutted PC, using open box to make removing/adding things easier.
PC boots to CD when HDD 1 isn't connected to SATA 0-6
PC fails to boot when it is.
Ubuntu doesn't recognize HDD in gparted, installation, or in fdisk -l.
I'm doing everything I can to just format this HDD and have it working.
Any suggestions are greatly appreciated and will be tested.

Took out bad HDD, used the other one and booted to LiveCD, ran sudo mkfs.ext2 /dev/sd-.
Fdisk showed the HDD at 915gb so I know it's it.
I believe after this it will be usable once more, I'll continue to update this until fully fixed.

Edit--
Fully fixed, installed 15.04 over the corrupted drive after formatting 2 times.
Added solution in q

---

