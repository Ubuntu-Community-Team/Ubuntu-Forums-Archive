---
title: "Resetting hard drive partitions"
date: 2013-09-30
forum: General Help
---

### Post by flyfishingphil on 2013-09-30
I'm sure it's here somewhere but I can't find what I want to know in the searches so thought I'd start a new one.

Currently have the HD on my laptop partitioned with Vista in one and 12.04 in the made. Ran a quick check regarding how it's set up and here are the results:

[I]Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs            diag
 2      1574MB  76.6GB  75.0GB  primary   ntfs            boot
 4      76.6GB  242GB   166GB   extended
 5      76.6GB  239GB   163GB   logical   ext4
 6      239GB   242GB   3082MB  logical   linux-swap(v1)
 3      242GB   250GB   7779MB  primary   ntfs            hidden[/I]

Considering upgrading the Vista to Win7, 64 bit, but don't know if there is enough space or how to reset the partitions, or even how to read that correctly, but I think I split it pretty even when I originally set it up. Don't remember if I did the initial partition effort using Vista but maybe somebody can read that and point me in the right direction for expanding/reducing. (According to one test it said that the system is workable for 64 bit Win 7 may look into changing my 12.04 to 64 bit too. Is it markedly faster in 64 over 32 or is there a special benefit going to go 64?)

I looked at it in Vista but was only given the options of extending the Vista side and removing the Ubuntu side.

Any help, written for the computer dummy, will be greatly appreciated.

ffp

---

### Post by Petro Dawg on 2013-09-30
64 bit can utilize more RAM, so if you have more than 3 Gig its worth installing, otherwise you will probably not see much of a performance boost.  Also some new software now (at least in Windows) will only run in 64 bit.  I haven't noticed this issue yet in Ubuntu though.

Also, it's generally recommended to install Win7 first (let it have the entire hard-drive), then resize the Win7 partition from within Win7.  Then install Ubuntu. 
 
Trying to install Windows after Ubuntu has been known to be problematic at best.

---

### Post by flyfishingphil on 2013-09-30
I have the drive partitioned and have been using both the 12.04 and Vista (for some business needs) for some time now. The main reason to upgrade to Win7 is having lots of problems recently with Vista.

Just did some research and saw reference to gParted. Can I download that and resize the partitions in existence or do I need to do a full backup on both, do a total format and start over?

---

### Post by Petro Dawg on 2013-09-30
Always back up anything important before messing with partitions.  Personally I find fresh clean installs take less time and are more stable than trying to modify an existing one, but that is up to you.  

I would back up everything, install Win7, then immediately resize Win7 using the included Disk Management Tool (do this right away to prevent fragmentation of the partition limiting how much you can shrink the partition), and then install Ubuntu alongside Win7.

And if this is a desktop, I really prefer installing 2 separate harddrives and running Windows on one and Ubuntu on the other, its super easy to do, doesn't require messing with partitions, and has worked perfectly for me for years now.

---

### Post by DuckHook on 2013-09-30
*Petro Dawg's* advice is both pithy and accurate. Win 7 is snooty and insufferable when it comes to owning the HDD, so attempting to upgrade from Vista with your current hybrid partitioning (because it includes Ubuntu already) will likely not only fail, but could hose your Ubuntu install altogether. No matter which method you choose, you MUST make backups first (read my signature).

Since the other options will likely end up being more trouble than they are worth, I would back up everything, nuke the HDD and install Win 7 letting it have its petulant way. Win 7 does not play nice with *gparted* partitions. Then follow *Petro Dawg's* procedure by using Win 7's tools to resize partitions, then install 12.04 as the last step. [Here]("https://help.ubuntu.com/community/WindowsDualBoot") is a guide to doing it properly along with far more detailed explanations as to why Windows is so finicky.

---

### Post by oldfred on 2013-09-30
Generally use Windows tools for Windows and Linux tools for Linux.
Windows 7's default install is to two partitions. The first is a 100MB hidden boot partition with the recovery console. But it is primarily to let you encrypt the main install as the Boot partition cannot be encrypted. If you just install to the existing NTFS partition with the boot flag, it will install to that one partition. Then make a repair CD or flash drive so you have a way to repair Windows. 
In Linux your liveCD or flash drive is also an emergency repair boot system, but Linux can only repair minor Windows issues and most need a Windows repairCD. Gparted is in Ubuntu liveCD or you can download it as a spearate repairCD.

If you have installed a lot of applications and will want those also in your new install make a list with dpkg. Backup /home or create a new /home with gparted and copy all current /home into new partition if you have room.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by flyfishingphil on 2013-09-30
Not a desktop. As it shows above it's a 250 GB in a Toshiba Sat.

You sound right as far as doing a total format, install the Win then do a quick partition and reinstall the 12.04. Probably the cleanest way to do it and I've got a new 1TB external to save the backup to. Just have to remember how to do a complete save and reinstall when done with the installation of both.

I've spent the last 2 days trying to figure out what all the problems are with the Vista, set up and make full operational a new tablet, correct problems with the router and prepare for a road trip. Think I'll take a break from the electronix and go to work on the trip prep.

Will check back in later.

Thanks again for the advice.

ffp

---

### Post by Petro Dawg on 2013-09-30
> **flyfishingphil said:**
> Not a desktop. As it shows above it's a 250 GB in a Toshiba Sat.

Wow, you don't expect me to read your entire post, do you?  :lolflag:  I have a bad habit of skimming.

---

### Post by flyfishingphil on 2013-10-01
(LOL) That's the same reason I spend so much time here trying to figure out how to do or what I did wrong. Old head injury makes it hard to read some things that are too long. Add to that my age and it's self explanatory!

I'm to the point I spend a lot of time thinking about the "here after". That has nothing to do with religion! It's when you get to the point you walk into a place then spend the next 5 minutes standing there asking yourself "What the hell am I here after?"

---

### Post by flyfishingphil on 2013-10-01
Thanks oldfred, looks like you have some good practices listed there so that is what I'll do when I get back from this short road trip. Knew I bought that 1TB external the other day for a reason.

ffp

---

### Post by Bucky Ball on 2013-10-01
*Thread moved to **General Help**.*

---

### Post by flyfishingphil on 2013-10-05
Getting shaky in the knees and weaker than before in the brain. Insanity is just one more re-start from taking over!!!!!! Back to page one on this one!

Received the disks, both 32 & 64 bit, for Win 7, but can't figure out how to do a total format of the HD so I can start over. I think what I did before, when I installed 12.04, was partition the disc under that then added Vista. From the actions I get under Vista, which doesn't do any thing regarding formatting the whole drive and starting over, I think I need to get in and do the total format from 12.04.

How do I do that?

Here is a terminal entry that may help find the answer: (Let me know if there is anything else I need to run for info)

[I]sudo fdisk -l
[sudo] password for flyfishingphil: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa275a313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   149573057    73249505    7  HPFS/NTFS/exFAT
/dev/sda3       473202688   488396799     7597056   17  Hidden HPFS/NTFS
/dev/sda4       149573630   473202687   161814529    5  Extended
/dev/sda5       149573632   467181567   158803968   83  Linux
/dev/sda6       467183616   473202687     3009536   82  Linux swap / Solaris

Partition table entries are not in disk order[/I]

---

### Post by oldfred on 2013-10-05
Windows will just install to a NTFS formatted partition with the boot flag.
Do you want to start over?
You can use gparted to delete all partitions if you have backed up everything. 
Or you can totally erase drive so no remaining data is on drive. 
Or you can just erase partition table with command line (Which is what gparted is doing).

---

### Post by flyfishingphil on 2013-10-06
Finally figured it out and did a total clean up and install of Win 7. Now I just have to figure out how to do the partition part so I can put 12.04 back in.

---

### Post by Bucky Ball on 2013-10-06
If you have just installed Win7 to a partition big enough to hold it (say 30Gb) and left the rest of the drive as 'free space' then you can create partitions at the partitioning section of the Ubuntu install by choosing 'Something Else'.

If you installed Win7 on a partition that uses the whole drive, then get into Win7, shrink the partition to what Win7 needs leaving the rest free space, and do what I just suggested while installing Ubuntu. ;)

---

### Post by flyfishingphil on 2013-10-06
OK. Managed to do a partition and now have drive F: to install Ubuntu 12.04.3 in but how do I do that? Have it on disc, put it in the disk drive but had no option offered to install. Been, primarily, Ubuntu for several years and have never messed with the Win 7 system before so I'm at a complete loss as to how to continue.

---

### Post by Bucky Ball on 2013-10-06
You didn't read my post? (Check #15 again.)

If you made a partition for Ubuntu with Windows you wasted your time because it will be NTFS or FAT, neither of which you can install Ubuntu on. Ubuntu needs to be installed on an EXT partition, which only it can make (and does so during install - like I said, shrink Windows and leave 'free space' where you are going to put Ubuntu, not a partition for it or anything else). ;)

When you put the install disk in and boot from it, what do you get if you get no options? You should be getting 'Try Ubuntu' 'Install Ubuntu' and some other options or going straight to a desktop which has a 'Install Ubuntu' icon on.

---

### Post by oldfred on 2013-10-06
Also if you create partitions with Windows it may convert to dynamic partitions which does not work with Linux and does not work with some Windows tools. 
You have to keep the 4 primary basic partitions and then convert one primary to an extended partition to have logical partitions.

---

### Post by flyfishingphil on 2013-10-06
> **Bucky Ball said:**
> You didn't read my post? (Check #15 again.)

If you made a partition for Ubuntu with Windows you wasted your time because it will be NTFS or FAT, neither of which you can install Ubuntu on. Ubuntu needs to be installed on an EXT partition, which only it can make (and does so during install - like I said, shrink Windows and leave 'free space' where you are going to put Ubuntu, not a partition for it or anything else). ;)

When you put the install disk in and boot from it, what do you get if you get no options? You should be getting 'Try Ubuntu' 'Install Ubuntu' and some other options or going straight to a desktop which has a 'Install Ubuntu' icon on.


What I planned to use as Drive F is listed as "Free Space". Tried boot with 12.04 disc in but it sets there a minute with the "-" flashing in upper left corner then goes on into Windows. Don't see the options, or the "Install Ubuntu" icon on the desktop.

Do I need to delete it from the DVD and do something there before trying a new download of Ubuntu? Everything seems to be correct but apparently something isn't.

---

### Post by oldfred on 2013-10-06
Do you get the purple screen with tiny icons of a person & keyboard at the bottom? Press any key, then f6 and choose nomodeset.
Otherwise it may be a bad download. You can check with md5sum.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

      
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Bucky Ball on 2013-10-06
... and sounds silly, but make sure you are booting from the CD. You need to set this in the BIOS or 'change boot device' by hitting a key at boot, sometimes F12. ;)

---

### Post by flyfishingphil on 2013-10-07
OK. Have it installed and working. Now I need to go back in and check the HD to see what it did there to install it. Had a "Free" sector set aside but haven't checked yet to see if it went there.

For those following to see what works keep these tips in mind:

Download your Ubuntu program from Ubuntu only. I hadn't noticed that I was downloading from somewhere else and wasn't getting the entire file.  (Usually provided somewhere between 682MB and 687MB. Total download is 707 MB.)

For easy to follow instructions take the time to go directly to Ubuntu and download and print the instructions there. Simple, easy to read and follow instructions. Not a lot of confusing info that refers to things that you may not know what, where or how to get to. (I got the "Install Ubuntu after Windows". REAL EASY!)

I'll keep this open for right now and add more as I find the easiest way to do it.

---

### Post by flyfishingphil on 2013-10-11
Nothing to add so this one is solved.

---

