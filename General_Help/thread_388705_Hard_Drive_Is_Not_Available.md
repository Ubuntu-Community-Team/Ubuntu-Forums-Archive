---
title: "Hard Drive Is Not Available"
date: 2007-03-19
forum: General Help
---

### Post by n8oay on 2007-03-19
I have a ***VERY* frustrating** issue that I have been fighting for over a week...I am having a problem in trying to make a second hard drive available for data and have not had any luck getting help on the Ubuntu Hardware & Laptops forum - realizing that this is a software problem and not a hardware problem, I am posting it here. 

I have tried following the steps outlined at [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) modifying the commands to suit my needs. I have also tried suggestions from other sources including the "Ubuntu Linux Bible" (admittedly, this book is way over the lead of this Linux Rookie), messages on various other Ubuntu Forums including [http://www.ubuntuforums.org/showthread.php?t=388203&highlight=permission](http://www.ubuntuforums.org/showthread.php?t=388203&highlight=permission) and probably some that I can not remember. So far, all I have succeeded in getting is a message during boot a couple days ago that hda1 had been mounted 30 times without being checked and giving me the option to check the disk, which I did. Several of the commands that I tried resulted in error ```
mount: mount point /home/n8oay/data does not exist
``` and various permission related errors. It makes no difference to me whether /home is moved the hda1 or hda1 appears as a Data folder under /home/n8oay. Regardless of what I do, when I check Properties on /home after trying various commands, I can tell from the amount of available free space that hda1 is not there. If I try to go to hda1 in Konqueror or Nautilus, I get a message telling me that I do not have permission to go there.

I do not understand what the problem is with doing such a simple task as having a second hard drive available for data storage. I have been using computers since MS Dos 2.0 and Word Perfect 4.1. I am no dummy. I can read, and I can follow instructions, so what is the problem? This issue has given me a lot of insight into why so many people will not use Linux, and has me thinking maybe I should have stayed in that group. Repartitioning and formatting a hard drive that had previously been used as a boot drive while dual booting and trying various distros, and making that drive available for data should not be this difficult!

I am using Ubuntu 6.10 (running both GNOME and KDE) which is on drive hdb, and was installed using the default "take over the entire drive" option. Xandros 4 Home Premium Edition (yes, this was a purchased boxed package because I wanted the printed documentation) was the last OS installed on drive hda (Xandros replaced Linspire 5.0 which came on a DVD with the "Linux for Dummies" book), and was working correctly while dual booting with Ubuntu. I booted to the Ubuntu DVD to repartition, and formatted the drive in ReiserFS. I decided to go with Ubuntu because I found the customization of both Linspire and Zandros to be too restrictive - neither will run some applications that are not installed from their respective networks.

---

### Post by confused57 on 2007-03-19
You'll find some excellent explanations of how to mount different filesystems here:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

I have a 100 Gb /media/data partition that I use for storing files...it's ext3, but the above link also has instructions for mounting other filesystems.  It's totally separate from my /home partition & is used only for data storage.

---

### Post by n8oay on 2007-03-19
Well, that did not work, and I could not get into KDE after editing fstab and rebooting. When I go into GNOME, I get a Crash Reports with the following errors:
```
Sorry, the program "ksplash" closed unexpectedly

Sorry, the program "kdeinit" closed unexpectedly
```

Fortunately, I have both GNOME and KDE (installed Kubuntu Desktop) enabled, so I was able to restore fstab to it's original condition and then was able to get back into KDE.

Here is what I did, following the instructions in the Edgy Eft UUID section of [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

I opened fstab with 'sudo gedit /etc/fstab', added a line for the second drive, and rebooted, and could not get into KDE

Here is what fstab looked like before I edited it:
```
Before Edit:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=340a4fb0-3886-4a64-b8c2-80b597ee151a / /media reiserfs auto rw,user,noauto 0 0
# /dev/hdb1
UUID=990bbbe4-d46d-4ba4-81e8-defdf67c9298 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=bd34408d-3117-4e83-9357-de84d1997e22 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

This is what I entered into fstab (the last 2 lines):

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=990bbbe4-d46d-4ba4-81e8-defdf67c9298 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=bd34408d-3117-4e83-9357-de84d1997e22 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hda1
UUID=340a4fb0-3886-4a64-b8c2-80b597ee151a none            reiserfs    sw              0       0
/dev/hda        /media/hda1     auto    rw,user,noauto  0       0

```

What did I do wrong?

---

### Post by confused57 on 2007-03-20
You can use a live cd or from your (K)ubuntu installation, open a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

This will show your partition tables.

I noticed in your fstab entry:
```
# /dev/hda1
UUID=340a4fb0-3886-4a64-b8c2-80b597ee151a none            reiserfs    sw              0       0
/dev/hda        /media/hda1     auto    rw,user,noauto  0       0
```

The last line /dev/hda...., you're trying to mount the entire hard drive(or the mbr), you have to have separate mount points for each partition(not an entire hard drive).

Your UUID for /dev/hda1 may be different from what it was initially, see the hermanzone link for determining the current UUID:
```
sudo vol_id -u /dev/hda1
```

I'm definitely not an expert using UUID's...you might want to read back over Herman's instructions.  You actually don't have to use UUID's in your fstab.

I would think something like this would work:
```
# /dev/hda1
UUID=340a4fb0-3886-4a64-b8c2-80b597ee151a /media/hda1 reiserfs defaults 0     2
```

I assume you've made a directory in /media for a mountpoint for /dev/hda1:
```
sudo mkdir /media/hda1
```

---

### Post by n8oay on 2007-03-20
I have already tried booting with the DVD, but just to be sure I did not miss anything or type the commands wrong, I printed the page out (instead of switching back and forth with the KVM switch) and tried again. Still no luck. And looking back on it, I really think there may be at least one step missing from the instructions on [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) - it seems to me like all of the changes I was making was being made only on the Ramdisk that is created when booting from a Live DVD (I assume that creating a Ramdisk is how the Live DVD works). After rebooting to the hard drive, no changes had been made to hda, based on the Date Modified that I can see in Konqueror. So I started going through the instructions in your last post, starting with the last line ```
sudo mkdir /media/hda1
``` to verify that I had added one directory to hda - and I got an error indicating that I did not have permission to do that. This is ***VERY FRUSTRATING!***

I thought I left behind the need to edit text files to get a computer to work when Windows 3.1 and Windows 95 became past history. Since Ubuntu is touted to be the most popular distro, topping Fedora and SUSE, I expected it to be much more user-friendly than it has turned out to be. I decided to try Linux so that I could have a computer that is not bogged down with anti virus, anti spyware, anti adware, etc., etc. etc. programs running in the background. It appears to me that Ubuntu is quite capable of serving those desires, but otherwise is not yet ready for prime time. 

10 years ago, I would have been thrilled at the challenge of making this work (just so you know my background, I was a phone tech support rep for 8 1/2 years for an OEM, but my job was supporting the warranty on the hardware, not providing software support). But now, I no longer want to deal with the frustration of resolving this problem. I have spent at least 2 or 3 hours every evening after getting home from work for the last 6 days trying to fix this problem that is a no-brainer in Windows, and at least one other Linux distro. 

I have resolved the problem of trying to mount my 2nd hard drive under /home, but probably not in the manner that you want to hear about. I booted with Acronis Disk Director, deleted the partition on the boot drive, and installed Xandros 4. After completing the install, I booted into Administrator, completed the initial setup, then went to Storage Manager and had the 2nd drive set up as /home with 5 or 6 mouse clicks. I really don't want to use Xandros because of it's limitations created by the high customization, but right now for me, Xandros is the lessor of the two evils. I may try Ubuntu again at some time in the future, but it will have to wait until the next release. I am not the techy geek that I was when working as a tech support rep - I just want a computer that works. As long as Linux is a difficult to work with as Edgy Eft has been for me, it is never going to succeed at even dreaming of replacing Windows on the average home user. I consider myself to be a few steps above the average home user, but I just no longer have the patience to work through the kind of hassles I have had with adding a 2nd hard drive to Ubuntu.

---

### Post by confused57 on 2007-03-20
Sorry things didn't work out for you with Ubuntu.  If you were reinstalling, you could have easily installed Ubuntu on the same partition and during the installation process, you could have selected your 2nd hard drive partition as your /home mountpoint...an entry would have been automatically added to your fstab to mount it as /home. 
 Everyone has their preferences, but I personally wouldn't install /home on a separate hard drive...instead, as I've mentioned, I would create a separate data storage partition(or 2).  During installation, just type in a desired mountpoint(e.g. /media/data) for your 2nd hard drive partition...an icon will be automatically added to your desktop, an entry would then be automatically added to fstab, etc.

Doing it this way, there shouldn't be any reason to have to manually edit your fstab after installing Ubuntu.  As I've said, I'm no expert, and maybe don't fully understand your preferences & needs, nor your desired setup...this said, the above suggestions are the best I can offer, if you ever want to give Ubuntu another shot.

Hope to see you around again, using Ubuntu, or whatever works for you.

---

### Post by n8oay on 2007-03-20
> **confused57 said:**
> Sorry things didn't work out for you with Ubuntu.  If you were reinstalling, you could have easily installed Ubuntu on the same partition and during the installation process, you could have selected your 2nd hard drive partition as your /home mountpoint...an entry would have been automatically added to your fstab to mount it as /home. 
 Everyone has their preferences, but I personally wouldn't install /home on a separate hard drive...instead, as I've mentioned, I would create a separate data storage partition(or 2).  During installation, just type in a desired mountpoint(e.g. /media/data) for your 2nd hard drive partition...an icon will be automatically added to your desktop, an entry would then be automatically added to fstab, etc.

Doing it this way, there shouldn't be any reason to have to manually edit your fstab after installing Ubuntu.  As I've said, I'm no expert, and maybe don't fully understand your preferences & needs, nor your desired setup...this said, the above suggestions are the best I can offer, if you ever want to give Ubuntu another shot.

Hope to see you around again, using Ubuntu, or whatever works for you.

I was so aggravated when I posted that message that I forgot to mention that I did try to reinstall Ubuntu, but I did not do a format and reload. It still would not give me access to that hard drive. I took a half day off from work today fully intending to either fix it or nuke it. I made 3 failed attempts to mount the drive as a /data under /home, then booted to the Acronis CD. Like I said, 10 years ago, I would have enjoyed the challenge. After I made my last post, I nuked Xandros and installed Mandriva Free 2007. Like Xandros, I had that 2nd drive working with just a few mouse clicks. 

For Ubuntu to get me back, that ridiculous "sudo root" mode is going to have to be replaced with a real admin log on. Right now, thinking back, there may have been times that I thought I was in Root mode but was actually in User mode. That is a really stoopid way to set up an operating system IMHO. But for what it's worth, I had a problem installing Mandriva - it for some reason was not able to set up my Microsoft 5-button mouse during install...after the first reboot, I had to go into the control center using just the keyboard and set the mouse up, not a big deal but still something that should not have to happen.

---

### Post by youareno6 on 2007-05-01
I skimmed through the previous posts so if this was already discussed , I apologize. The problem is most likely the update to 7.04 uses new kernel modules to load disk devices. If you were to run an fdisk -l you would probably find scsi (sd) disks listed instead of IDE (hd) disks. This is causing a lot of havoc in the community. Basically, the new modules that are loaded see any disk as a scsi disk. So if you try to mount /dev/hda1 /mnt/point guess what...there is no more hda1. It most likely has been renamed as sda1. Now since the /etc/fstab uses UUIDs now, the system will most likely boot, but any manual changes you made will be broken. :confused: 

Good luck. I hope someone realized how much harm this change is going to cause.

---

