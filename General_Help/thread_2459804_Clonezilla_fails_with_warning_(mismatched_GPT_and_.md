---
title: "Clonezilla fails with warning (mismatched GPT and MBR partition)"
date: 2021-03-26
forum: General Help
---

### Post by Brent_Santin on 2021-03-26
I just finished setting up a new (to me) computer with a fresh installation of Lubuntu 20.01. 
I used the automated installer to install this OS over top of Windows 10 (so the computer is a total Lubuntu computer now - no more Windows). This created one big ~469GB partition on the boot drive.

After spending the past few days ironing out all the kinks, installing and tweaking my favorite applications, creating desktop launchers, etc. I got it to where I was happy, and decided to back it up with Clonezilla, which I've done many times before on previous computers.

However, this time Clonezilla failed to back it up with the following warning (ugh!):

> [FONT=fixedsys]This disk contains mismatched GPT and MBR partition: /dev/sda.
It will confuse Clonezilla and might make the saved image useless or fail to clone the disk.
You can use gdisk or sgdisk to fix this issue. E.G. if you are sure only MBR partition table is the one you want, you can run this command to destroy the GPT partition table while keep the MBR partition on table:
sudo sgdisk -z /dev/sdx
//NOTE// (1) Replace /dev/sdx with the above hard drive name. (2) ALL EXISTING DATA ON THE DISK WILL BE LOST IF GIVING WRONG COMMAND. USE THIS COMMAND CAREFULLY.
Please fix this issue then restart Clonezilla again.
Program terminated!![/FONT]

So it seems I cannot back up my computer. Also the warning message is **rather terrifying**, as I am not really sure what is going on or how to fix it. The little I can fathom is that there are tiny boot partitions on the hard drive to tell it where the larger sectors/partitions lie, and that there are two conflicting ones. I'm assuming one is a vestige of the old Windows 10 installation. Unfortunately, I don't know which - MBR or GPT - is the one to delete or if I even should, or how to. I dread messing up my hard drive and having to spend several days getting it back to where I finally had it.

Why did this happen in the first place?

I am a little out of my depth here. Could someone guide me through the process?  I'm not even sure if what Clonezilla is asking is the right thing to do. I've done a bit of Googling about the problem, and all suggestions give rather high-level instructions and warn about messing up one's hard drive. I've attached a screenshot of the Clonezilla error screen and a screenshot of my hard drive partition as shown in KDE partition manager.

Another thing that might offer a clue is that the Grub Boot Loader never shows up when I start this computer. It goes straight to the Lubuntu boot screen (Lubuntu Logo) and starts up. This is the first time I've seen this on a Lubuntu computer, and thought maybe it was a new change for Lubuntu 20.04, but now I'm thinking it is a symptom of the problem above.

This is a problem I really need some hand-holding to get through!  Thanks very much for any help you can offer.

[ATTACH=CONFIG]288188[/ATTACH][ATTACH=CONFIG]288189[/ATTACH]

---

### Post by oldfred on 2021-03-26
I typically recommend gpt partitioning, MBR(msdos) partitioning is now 40 years old.
Then only place you have to have MBR is with Windows when booting in BIOS mode.

Ubuntu works with UEFI or BIOS boot from gpt partitioned drives.
[http://www.rodsbooks.com/gdisk/whatsgpt.html](http://www.rodsbooks.com/gdisk/whatsgpt.html)

It looks like you had Windows in UEFI boot mode on gpt drive, but then installed in BIOS/MBR boot mode.
With gpt you have a backup partition table at end of drive, so if gpt protective MBR, gpt primary & gpt backup get out of sync, you have issues. Or if drive not correctly converted to MBR, backup gpt will not match.

Post this to see details, it may suggest similar command to repair gpt/MBR.

sudo gdisk -l /dev/sda

Most tools to convert from gpt to MBR or vice-versa erase drive. Gdisk or sgdisk is one of the tools that can convert in place, but backups are still required.

---

### Post by Brent_Santin on 2021-03-26
This is what was returned by [B]sudo gdisk -l /dev/sda

> Main partition table: ERROR
Backup partition table: OK

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 
[/B]
I did not dare enter any response until advised by this forum.

> Most tools to convert from gpt to MBR or vice-versa erase drive. Gdisk  or sgdisk is one of the tools that can convert in place, but backups are  still required.

I would definitely like to backup before repairing the boot record, but how can I backup when Clonezilla complains it cannot while the boot record conflict remains? Is there another way?

Thank you.

---

### Post by oldfred on 2021-03-26
I believe you can choose the MBR only choice, but still suggest backup.
Clonezilla is only one of many (maybe too many) choices with Linux.

I use rsync. I do not back up Ubuntu / (root), but do include some files from / that I have edited by copying into /home, so backup of /home & my data includes those files. I also export list of installed apps, to make it easy to reinstall everything.
If a server or a desktop with server apps, then you have additional folders in / that you need to include in your backup.

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) & 
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

### Post by Brent_Santin on 2021-03-26
Okay, I ran the sudo gdisk -l /dev/sda and selected option 1 (MBR). Here is the output.

> brent@i5tower:~$ sudo gdisk -l /dev/sda
[sudo] password for brent: 
GPT fdisk (gdisk) version 1.0.5

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Warning: Invalid CRC on main header data; loaded backup partition table.
Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!
Main header: ERROR
Backup header: OK
Main partition table: ERROR
Backup partition table: OK

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 1
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Model: ST500DM002-1BD14
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 9310DCF0-8DB9-4EA7-AC0B-A4EA0E7B3E3D
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7084 sectors (3.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       976768064   465.8 GiB   8300  Linux filesystem
brent@i5tower:~$ 


I still have to reboot and see if there are any changes, but am posting this immediately before rebooting.

(...to be continued in next post).

---

### Post by Brent_Santin on 2021-03-26
(...continued from previous post)

Well the system rebooted no problem. However, Clonezilla still reports the mismatch MBR / GPT partition error and will refuse to back up the drive.
I'm concerned about all the errors reported be gdisk.

What can I do next to remedy this situation?

Clonezilla talks about using the -z parameter with gdisk. That sounds drastic!

---

### Post by oldfred on 2021-03-26
Often after partition issues, you have to run fsck and reinstall grub. If it boots without issue, you probably do not need to reinstall  grub, but may need fsck?

Does gdisk show no error now?

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Brent_Santin on 2021-03-26
gdisk reports the same(?) set of errors as above:

> brent@i5tower:~$ sudo gdisk -l /dev/sda
[sudo] password for brent: 
GPT fdisk (gdisk) version 1.0.5

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Warning: Invalid CRC on main header data; loaded backup partition table.
Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!
Main header: ERROR
Backup header: OK
Main partition table: ERROR
Backup partition table: OK

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 

I am not familiar with fsck, but will analyze your instructions in the post above and follow them. I just am unclear about the following from your instructions:

>  To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted

Okay, so I boot from a live DVD, then from terminal type "sudo parted -l"

>  swap off if necessary, 

not sure what swap off means. Googled it: swap file off (**sudo swapoff -v /swapfile**), correct?

> change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p  tries fixes where response not required, Run both commands as they have  different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

So:
 sudo e2fsck -C0 -p -f -v /dev/<whatever drive label parted shows me>
sudo e2fsck -f -y -v /dev/<whatever drive label parted shows me>

I'll give it a try. 

By the way, running **sudo gdisk -l **with the system running (not Live DVD) I see:

> brent@i5tower:~$ sudo parted -l
[sudo] password for brent: 
Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4


Model: ATA WDC WD5000AAKB-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs         boot


The ATA ST500DM002-1BD14 is my boot drive with Lubuntu. The other drive is just a file storage drive (an archive of video and music).

Thanks very much for your help.

---

### Post by Brent_Santin on 2021-03-26
Okay...did as you instructed and only got as far as the first fsck command with the following error message:

> [FONT=courier new]lubuntu@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda
e2fsck: Bad magic number in super-block while trying to open /dev/sda                                                                                                                        
/dev/sda:                                                                                                                                                                                    
The superblock could not be read or does not describe a valid ext2/ext3/ext4                                                                                                                 
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4                                                                                                                 
filesystem (and not swap or ufs or something else), then the superblock                                                                                                                      
is corrupt, and you might try running e2fsck with an alternate superblock:                                                                                                                   
    e2fsck -b 8193 <device>                                                                                                                                                                  
 or                                                                                                                                                                                          
    e2fsck -b 32768 <device>                                                                                                                                                                 
                                                                                                                                                                                             
Found a dos partition table in /dev/sda [/FONT]

Just in case it means anything, sometimes when booting I see a whole list of APCI errors displayed, but the system still boots. Don't really know what that means. They go by too fast for me to capture them.

---

### Post by oldfred on 2021-03-26
With gdisk, you typically have to give a w (for write) after any updates or changes or a q (quit without changes).
So not sure if you updated or not?

---

### Post by Brent_Santin on 2021-03-26
Sorry, I did not understand what you were instructing about gdisk at first as this is my first time using that command. In the case where I entered** sudo gdisk -l /dev/sda **as instructed by you above, it did **not** provide the COMMAND prompt for me to confirmation either "W" or "Q". 
So no, I assume then it did not write. 

I did a little reading about gdisk and tried the following (omitting the -l parameter this time):

[FONT=courier new]> 
brent@i5tower:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Warning: Invalid CRC on main header data; loaded backup partition table.
Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!
Main header: ERROR
Backup header: OK
Main partition table: ERROR
Backup partition table: OK

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 1

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): n
Aborting write of new partition table.

Command (? for help): 
[/FONT]As you can see at the end there I pressed "N" to abort (out of caution). So at this point I'm to press "Y" instead to write, correct? Once I get your confirmation that I understand this correctly I will proceed. 

Thank you VERY much!

---

### Post by oldfred on 2021-03-26
Yes, that should work.

---

### Post by Brent_Santin on 2021-03-26
Well, I'm posting from my spare laptop now, because after doing that and rebooting all I get is a black screen with a flashing cursor. So I guess my boot record was corrupted?  Anything to do besides reinstalling Lubuntu 20.04 from scratch?

---

### Post by Brent_Santin on 2021-03-26
I'm just going to reinstall.

---

### Post by oldfred on 2021-03-26
As mentioned you may need fsck and reinstall of grub.
But if more than an hour or two trying to repair, then reinstall & restore from backup if quicker.

---

### Post by tea for one on 2021-03-26
> **oldfred said:**
> As mentioned you may need fsck and reinstall of grub.
But if more than an hour or two trying to repair, then reinstall & restore from backup if quicker.

I agree - after spending an hour or two trying to repair, re-install and restore backup is easier and less stressful.

When you boot into a live session, double check that you have booted in UEFI mode and then create a GPT partition table using gparted or similar partition editor.

Clonezilla will then have little reason to complain ;).

---

### Post by Yellow Pasque on 2021-03-27
FWIW, you probably should have selected option 2) GPT to restore the main GPT from the backup. You clobbered it using MBR.
I'm more familiar with this menu, where you would have chosen 'b' instead of 'f':
[http://rodsbooks.com/gdisk/repairing.html](http://rodsbooks.com/gdisk/repairing.html)

Sorry, I know hindsight burns..

---

### Post by oldfred on 2021-03-27
If a BIOS boot install on gpt partitioned drive, it would have a bios_grub partition. His screen shot did not show a bios_grub.
Or it would have given grub errors on install to gpt without a bios_grub and would not have been bootable.

I still suggest to use gpt and if UEFI system, use UEFI install to gpt drive. With UEFI you have to have a ESP - efi system partition, FAT32.

For several years when thinking about a new UEFI system, I partitioned with gpt, but put both bios_grub for current system but also an ESP, so I could move drive to new system & just reinstall grub to have it be UEFI bootable.

---

### Post by Brent_Santin on 2021-03-27
Okay, after a late night during which I *nearly* threw in the towel, I've finally got my system up and running. 

The whole problem (explained in my original post) was my lack of understanding of UEFI vs. BIOS and GPT vs. MBR. My old computer was from 2006, so still had standard BIOS/MBR. The new one is from ca. 2015, so knows has UEFI and knows how to deal with GPT boot records. I had never dealt with a computer that used EUFI and GPT before. 

Not knowing the differences, I chose to boot the Lubuntu Live installation from my DVD drive using the non-UEFI legacy mode (by hitting F12 at power-up and selecting that choice in the BIOS' boot priority menu).  Unfortunately, whatever mode you boot the installation disk in is the mode in which Lubuntu installs itself on the hard-drive (this was not obvious during the installation process, but even if it had been I probably wouldn't have caught-on given my state of knowledge at the time). So, by installing Lubuntu the "legacy" way I wrote a new MBR over top of Windows 10's GPT boot record. This caused the GPT/MBR mismatch Clonezilla was complaining about.

My solution (after trying several failed re-installs and buggering up the hard-drive completely by erasing partitions -- especially the UEFI partition -- and not understanding how to set them up again) was to restore the system to the way I had received it ---- with only Windows 10 on it (fortunately I had made a backup image of the hard-drive in this state). In doing so this also restored the EUFI partition I had wiped.

Next, I installed Lubuntu from the live DVD, this time making *SURE* to boot the DVD drive in EUFI mode (my BIOS boot priority selector has two choices for my DVD drive: EUFI and "non EUFI"). Lubuntu installed fine this way over top of Windows 10, and now when it starts it does show the GRUB menu, whereas under the old messed up Lubuntu MBR/GPT mismatch installation it did not!

So once I got the system up with a fresh install of Lubuntu, I wanted to immediately make a backup image of it (and test to see if Clonezilla worked this time).  At first I used a DVD of Clonezilla 2.2.x, which when booted in EUFI mode will not start (a screen comes up explaining that it failed to start). When the Clonezilla DVD is booted in legacy "non UEFI" mode it DOES start, but fails to back up the partitions to an image file (it tries, but reports that each partition did not back up properly - maybe because in this mode it does not understand EUFI/GBR?).

So then I made a DVD of Clonezilla version 2.7.x (the latest at the time of me writing this). It WILL boot into EUFI mode without complaint, and DOES back up all partitions properly in this mode. So I guess there have been improvements to Clonezilla since 2.2.x.

Whew! That took a lot of steps and a lot of aggravation. However it's probably worth it though as Lubuntu is properly installed and I now have a basic understanding EUFI and GPT.

---

