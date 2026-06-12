---
title: "Boot issues with grub rescue (dual boot)"
date: 2017-06-14
forum: General Help
---

### Post by grub92rf on 2017-06-14
I need some help to steer me in the right direction on how to resolve my  boot issue. It's a bit of a story so please read thoroughly (if you  don't mind).

First: I have a dual boot machine that I set up a  while ago. It has windows 7 and ubuntu 12.04 (or at least it did). 12.04  was updated from 8.04 by the way. I had grub (I think grub2) that would  handle which OS to load. I am somewhat of an intermediate linux user  though I don't understand exactly the nuances.
All was fine till  windows 7 started to act up a couple of days ago. It would start  initially and display the message "starting windows" after which the  screen went blank and it seemed to be doing stuff but it was useless  without the screen. Ubuntu was fine during this time. 
So to make a  long story short I trusted windows and clicked on the "recommended  repair". It of course did not repair anything but it messed up grub, or  MBR or partition table or whatever I don't know. Now when I started it  would display the message "error: file (might have been partition) not  found then next grub_rescue". So neither windows nor ubuntu would be  available to load.
The other day I read about boot repair so I  thought to give it a shot. I also have a 12.04 CD that I can boot from.  They seem to corroborate the information I am giving you.
Boot repair (also fdisk -l) found the following partitions on /dev/sda:

Output of sudo fdisk -l   
                      Blocks      ID     System
/dev/sda1     13GB          27    Hidden NTFS WinRE
/dev/sda2     100MB        7     HPFS/NTFS/exFAT
/dev/sda3     256GB        7     HPFS/NTFS/exFAT
/dev/sda4     196GB        5     Extended
/dev/sda5     3.7GB         82   Linux swap/Solaris

So  I did the recommended repair using boot-repair, however, it only  "found" the windows partition. I tried to load windows 7 and I had the  same problem that I had previously with the screen going blank (ok  that's a separate issue). I did load windows in safe mode and the video  comes back so I think I can probably manage that problem. The windows  files are there and all so no catastrophe there...
But I can't get my Linux partition at least I can't boot into it.

As  far as I can tell the windows partition is on sda3 and Ubuntu on sda4.  Now boot repair thinks the windows boot is in sda2. I think sda5 is a  swap space for Linux. This has been a while to setup so some of the  details are vague to me.
I am also looking at the partitions with  gparted which reports the same partitions except sda4 is reported as an  extended partition with unallocated 192GB and /dev/sda5 as unknown with  3.75GB as sda5 (so sda5 is reported as a subset of the sda4 partition).  sda1 is reported as PQservice with used 12.27GB (flags as diag). Now if I  had to guess sda1 was where I had put the linux kernels but I am not  sure. sda2 is system reserved and flagged as boot.
Also, there is an unallocated 1MiB besides all the partitions. 

Now, after boot repair I did the sudo mount /media/sda2 /dev/sda2 and then followed by this (or something very similar): 
sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/sdXThis brought me back to the beginning error of grub_rescue. 

Can someone help on what what's wrong now with my linux partition and how to recover what I had (dual boot)? Thanks a bunch

---

### Post by TheFu on 2017-06-14
Welcome to the forums.

1) Wrong subforum. This is where people post how-to guides for others to use, hence the name "Tutorials" A forum admin will need to move it. I would have used the "General" subforum for this post.

2) 12.04 support ended a while ago.  Move to 16.04 to get the best help. Always run a supported release. Always.  Many versions of 12.04 haven't been supported for a few years - that means no patches in all that time. Very dangerous. There are some nasty remote execution bugs that would impact unpatched systems.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) has a table of the supported release dates. Look through it and learn the pattern.  If you stay on .1 of the April even-year releases, that provides the most stable install for the longest support period.

3) **boot-repair** has an option to capture boot information about the machine and provides the URL. Please post that URL to get factual help.  Some of what you've written makes sense, but not all of it. We need facts. That URL will provide the facts.

What I'd suggest is that you get 16.04.1 in the flavor you prefer.  Create a bootable flash drive or CD with it, boot off that, install boot-repair in the live-CD session and run it. It is 4 years newer and might handle things better.  When it creates the URL, post it here if it doesn't magically fix stuff.  Boot repair had an easier time pre-UEFI. Things get complicated fast now.

The fdisk -l doesn't show any Linux partition, BTW.  Also, the "extended" partition is a container for logical partitions which must have higher partition numbers (5+). sda4 cannot be used directly. Wikipedia has more on these partition types, if you care to know more.

---

### Post by oldfred on 2017-06-15
Moved to General Help forum.

I bet the Windows repair worked just like Windows updates to Windows 10 has done on BIOS/MBR configurations.
It just forgets to write the Linux partition in the extended partition back into the partition table when it updates.
Data is all there, some have recovered & just booted, most have had to reinstall grub.
But you need a current version of Ubuntu to have correct tools as older versions on 12.04 disk do not have all the updates. And grub reinstall would not work as repositories are closed.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

You can use parted rescue or testdisk.

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 
      Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[URL="http://ubuntuforums.org/showthread.php?t=2290190"]http://ubuntuforums.org/showthread.php?t=2290190
[/URL]Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) [URL="http://ubuntuforums.org/showthread.php?t=2290190"]
[/URL] 
Then use Boot-Repair to restore grub2's boot loader to MBR.
      How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by grub92rf on 2017-06-15
This looks the same as my problem. First, thank you
I got a 16.04 live CD and typed what you recommended.

Then, the print command gave this:

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD5000BEVT-2 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system  Flags
 1      2048s       27265023s   27262976s   primary   ntfs         diag
 2      27265024s   27469823s   204800s     primary   ntfs         boot
 3      27469824s   564340735s  536870912s  primary   ntfs
 4      564342782s  976771071s  412428290s  extended
 5      968914944s  976771071s  7856128s    logical

It looks like sda5 is a logical partition inside sda4. I understand prior poster said sda4 is a "container" for logical partitions but I know that the 2 large partitions (~200GB) contain the respective files for windows and the other for linux. I mean the majority of files/programs.
Assuming I need to rescue sda4 and (I am guessing sda5 with it). It's confusing because there are really 4 partitions? Is this because there's a limit of 4 partitions per HDD? 
I am trying to learn a bit more as I do this.
Assuming I use parted rescue what are the numbers I need to enter in my case? 564342782s  976771071s?
See someone said this in one of the forums listed:

********************************************************************
sudo parted /dev/sda unit s print //this printed the current partition table 
sudo parted
unit s
rescue
Start? //Here I entered in 1 sector after the extended partition
End? //Here I entered in 1 sector before the swap parition
*****************************************************************
Why the 1 sector difference?
While another post said this:

******************************************************
Many thanks! It seems I was not looking in the right threads.

Finding my missing partitions was easy, using parted:
Code:
 	$ parted
$ unit s
$ rescue [start of sda4] [end of sda4] 
It found my linux partitions and I had to do it again for my linux  swap partition (starting from the end point of linux partition to the  end point of sda4).
****************************************************
One more question regarding the partition table. When I do the backup, assuming I am running from live CD isn't the backup lost
if I reboot? Should I back it to a flash drive? Sorry I am not using a live USB.
Thanks again,

---

### Post by oldfred on 2017-06-15
If you use live installer to back up partition table save it to another device, if your system is not using a live installer flash drive with persistence or some place you can save data.
The missing partition is from start of extended partition to start of what now is sda5 or partition that is already inside your extended partition. 
Partitions have to have at least one sector between them. If you have several partitions, not sure how parted rescue separates them. But each partition does have data indicating start & end.

MBR has a limit of 4 primary partitions. And one primary partition can be converted to the extended partition to act as a container for logical partitions. No matter which primary partition is the extended partition, logical partitions then always start as sda5. If you still have an sda5, it may have been sda6 and got renumbered when Windows rewrote partition table.

---

