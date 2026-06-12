---
title: "grub meltdown or festive virus?"
date: 2018-12-21
forum: General Help
---

### Post by Timothy Taylor on 2018-12-21
I got an error message on boot yesterday - something about the Kernel needing to be loaded first - and "press any key to continue".  
Pressing any key only produced the same message again.

I restarted my PC and tried booting the next entry (previous version of 18.04) in the GRUB menu: this produced a different error message - something about "ELF magic" - but this time Pressing Any Key actually booted my system.

I gather that both these messages are produced by GRUB, so the Xmas virus theory was dismissed.  I ran Boot-Repair.  This annoyingly re-ordered the GRUB menu, making 16.04 the default instead of 18.04.  Choosing 18.04 merely produced the same behaviour as before, except that I had more keys to press to get options from the GRUB menu!

I ran Boot-Repair again, choosing "advanced options" = 18.04 as default OS and to reinstall GRUB and kernel.
That seemed to do the trick, except that now my system boots in *extremely low-res* graphics, won't detect my monitor nor offer increased screen resolution.  The GRUB menu no longer has options to boot earlier versions of 18.04, so I'm stuck.

I don't want to have to reinstall Ubuntu again and then have to spend days getting my apps & settings back.  Is there any automated "Ubuntu Repair" which will get my system back the way it was?  My last backup was about 2 weeks ago, so reinstalling 18.04 and copying files from USB HDD would be tedious, painful and I would lose weeks of recent work.

---

### Post by oldfred on 2018-12-21
What brand/model system?
What video card/chip?

Did you get a kernel update, but have installed nVidia directly from nVidia with .run file? That seems to be your symptoms. 
The .run file has to be reapplied manually to every new kernel, that is why we suggest only using Ubuntu repository or ppa.

Boot-Repair defaults to first install it sees, you have to use advanced options and choose correct install, if you have more than one.

Post link to summary report from Boot-Repair.

---

### Post by Timothy Taylor on 2018-12-22
I'm not sure what has happened, but today my system gets as far as the Mate logo and cycling "timer" dots and just stops: no progress to the log-in screen.  The only way out is ctrl-alt-del.
Yes, I have an Nvidia graphics card and was using the Nvidia driver

My system is based on Gigabyte 78LMT-USB3 mainboard with AMD CPU, 4GB RAM, Nvidia geforce 210 graphics card.

I'll try Boot Repair again later.

---

### Post by Timothy Taylor on 2018-12-22
Boot Repair report here:
[http://paste.ubuntu.com/p/KV9w57sYmy/](http://paste.ubuntu.com/p/KV9w57sYmy/)

---

### Post by Timothy Taylor on 2018-12-22
I had disconnected my old HDD with 16.04 and tried Boot Repair again, which generated the report above.
I subsequently tried the "advanced options" boot and left it running. This revealed a screen where various "**** not found" errors, etc., were s-l-o-w-l-y listed.  I was just about to give up and switch off when it said something about "giving up" and then my system booted normally!

Not cured though - restarting the PC gives the same problem as before.  Life is too short to wait ~ 20 minutes to start my PC!

---

### Post by oldfred on 2018-12-22
It looks like the motherboard is the newer UEFI that has CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Your install is BIOS with gpt partitioning and you have the required bios_grub partition for BIOS/CSM boot.

Did you update UEFI/BIOS? Or change to UEFI boot?
Elf issue is often using wrong boot mode, so system is trying to boot in UEFI mode and you have CSM/BIOS install.

With old BIOS installs, there used to be an issue of large / (root) partitions where kernel would be  beyond certain old BIOS limits on drive. Have not seen that with newer UEFI systems. But some UEFI using CSM may emulate BIOS too well?
I typically recommend smaller /  of 25 to 30GB and large /home or data partition(s) for rest of drive if on a larger drive.

---

### Post by Timothy Taylor on 2018-12-22
Thanks for your reply.

> Did you update UEFI/BIOS? Or change to UEFI boot?
No.  I must have changed the boot order in BIOS when I added the 3T HDD about 2 months ago, but no updates or other changes.  I recall using Boot Repair to coax my system to boot from the new drive back then, but my PC had been running trouble free ever since.  This problem has came out of the blue.

> I typically recommend smaller /  of 25 to 30GB and large /home or data partition(s) for rest of drive if on a larger drive
/?  Is that /dev/sda1 ?

I recall using GParted to maximise usable disk space when I installed 18.04 and /dev/sda1 is just 1.0 MB.  If /dev/sda1 should be 25-30GB, then that might be the problem?

---

### Post by oldfred on 2018-12-22
Your sda1 is the bios_grub partition. That is just unformatted space for grub's core.img file for BIOS booting. Normally with newer systems that are also UEFI, I suggest both the bios_grub if you want BIOS boot and an ESP - efi system partition for UEFI boot. You do not have to have both, but if you create both and then later want to change boot mode, you do not have totally reconfigure drive with lots of backups(which you of course do anyway) and repartitioning.

You only have one system partition sda2 and that is your / (root) partition. Since you have no other partitions, /home is a folder inside your / partition. If a newer user, but understand a bit about partitions, you may want a separate /home partition.

Many prefer separating system from data. I did that years ago with Windows, even before XP. I would keep c: as system and have data in other partitions. But newer Windows made it difficult as many programs auto saved data into system folders. And programs were not consistent. Backup was more difficult as data was in various places.

---

### Post by Timothy Taylor on 2018-12-23
Thanks for the explanation Fred.

If I've understood what you say, I should create a new partition for my /home directory, leaving ~ 30GB for /root ?

Now that I know that my system will boot after some time, I can back up my data and reinstall 18.04 at leisure.  
I was wondering if Ubuntu will do equivalent of "repair-install" like XP used to do, which preserves files & settings.  From what you say, it sounds like I may do better starting from scratch and paying more attention when I format and re-partition my HDD.

Thanks again.
TT

---

### Post by oldfred on 2018-12-23
If you have done some configuration & installed some apps, it is time to backup.
You user settings are in /home in hidden files & folders, start with a . (dot). You can turn on/off show hidden files in file browser.
And if you have installed a lot of apps you can export the list of all apps & reinstall. It only will install those not part of default install.
Only if you install server type apps like data base or web apps may you have folders in / (root) that you may also backup.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[URL="http://ubuntuforums.org/showthread.php?t=2236636"]http://ubuntuforums.org/showthread.php?t=2236636
      [/URL]
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428) 
    
 My rsync backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5) 


If you run this, you will see how much of / you have used.
df -h
Then you can see how much each folder in / uses, so you can see /home is probably most of it.
Shows 20 largest folders:

 sudo du -ahx / | sort -rh | head -20

---

### Post by Timothy Taylor on 2018-12-23
Thanks for a very informative reply.

> **oldfred said:**
> You user settings are in /home in hidden files & folders, start with a . (dot). 

User settings?  Does that include HDD information?

When I installed 18.04, I used grsync to copy my home folder to the new drive.  Maybe this explains the U/EFI issues?

---

### Post by oldfred on 2018-12-23
Your grsync should have just copied data, depending on settings.
That would not not be related to UEFI boot.

Only if you did an image copy of a BIOS/MBR based partition to an UEFI/gpt based partition would you corrupt a drive and cause all sorts of issues. The gpt partitioning system has GUID in primary partition table, backup partition table and the partition. If they get out of sync that causes corruption. 
But that is not ELF magic which is normally wrong boot mode in UEFI.

---

### Post by Timothy Taylor on 2019-01-03
> **oldfred said:**
> You only have one system partition sda2 and that is your / (root) partition. Since you have no other partitions, /home is a folder inside your / partition. If a newer user, but understand a bit about partitions, you may want a separate /home partition.

I wiped my HDD, re-partitioned for a /root partition of ~ 50GB, the rest as /home, but now I'm stuck.

I had thought I could move /home in Caja with cut & paste and make a link to put in /root, but it won't allow that.
How do I get the /home folder in a new partition?

---

### Post by oldfred on 2019-01-03
You have to copy data into your new /home.
And then add the mount into fstab.
Details here, you can skip most of the steps.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving
[/URL]
 Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]
[/URL]

---

### Post by Timothy Taylor on 2019-01-04
Thanks Fred. 
I suspect that various issues have been triggered by my BIOS battery failing = 2V!  I've had sound card problems, likely due to default settings being loaded with on-board sound enabled. I've replaced the battery, done a fresh install and everything's working nicely.  I'll try the separate /home set-up when I've caught up with everything else.  Thanks again.

---

