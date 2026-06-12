---
title: "no such partition error"
date: 2022-07-02
forum: General Help
---

### Post by jgw on 2022-07-02
I got the no such partition error.  

The boot disk is a 3tb disk

I have found a whole lot of solutions but they are all kinda strange to me.  My main problem is that they say to boot up with a usb stick and then start.  OK, I did that.  then it said to do a fdisk-l.  Then they all got down to the nitty gritty.  My problem with all the solutions is very simple.  When I booted up with the stick, it bootted up to the stick.  I could access the offending disk but I stopped because it seemed to me that they were dealing with the stick and not with the drive with the grub file on it.  This didn't make any sense to me.  First i thought they were moving the grub from the stick but after reading further that would be wrong.  I am, obviously, confused.  the other problem I have is that most of the solutions, on the net, kinda mandate that you also have microsoft on your system, I don't.  I don't think its necessary but I thought I would ask.  

It just dawned on me.  How should I move my terminal to another drive?  I used the program that makes such sticks so I have a stick from which I can install ubuntu but I don't know how to tell it to boot and move to the other drive as well.  

Anyway, could somebody tell me if I should take the terminal to the offending drive before I start finding grub, efi, stuff, etc?

Thank you..........

---

### Post by oldfred on 2022-07-02
If starting with a new blank drive, the fdisk will not show anything. The drive is blank and has no partitions to show.
I do prefer to partition in advance, if  a new drive, but you can partition as you install. 

Since drive is over 2TiB, you have to use gpt partitioning. You can boot in live mode & use gparted to create partitions.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

What motherboard? Some need UEFI settings changed.

If UEFI system, the minimum partitions you need are an ESP & / (root). But with that large of a drive, would not recommend a / that large.
Ubuntu now uses snaps which take a lot more space, but I do not allow snaps on my system and use Kubuntu which is not as large as Ubuntu. My system is about 10GB in a 30GB partition. I then have all data normally in /home in separate data partitions. I also still have unallocated space on my drive for future use.

Once you have partitions, you have to use Something Else install option to chose & change existing partition to be ESP & /. If /home wanted as a separate partition, you also choose it during install.

since you have nVidia, you also need to choose Safe Boot and to install restricted drivers to get nVidia driver installed. Otherwise you have to use nomodeset boot parameter in grub menu and manually install nVidia driver from Ubuntu repository.

Some older threads. With newer Ubuntu some settings may not now be needed.
GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by yancek on 2022-07-03
Is there anything on the 3TB disk?  Any operating system (if so, what?) or data?
Are you using a live Ubuntu USB to install Ubuntu?  If not, what were you trying to do when you got this error?  Which partition was it, did it show a UUID?  If it did, run sudo blkid and compare the warning UUID to the blkid output to see if that partition exists. 

What exactly were you trying to do when you got the error is the importantit question.  Install Ubuntu or boot it (or another Linux OS) from the 3TB drive?

---

### Post by jgw on 2022-07-03
Thank you for the replies!

apologize for not giving enough information.  My motherboard is a gigabye ga-f2a78m-hd2 the 3tb hard drive holds the boot partition.  I am booting with a memory stick which was created with startup disk creator.

Since the boot stick can also install a ubuntu system I am considering doing that to another drive and then access the disk with the problem and move stuff from that drive to the new one.  The offending drive is also completely backed up so I can move stuff to the new drive as well.  This would solve my problem and, I suspect, save me a lot of grief.  

My current problem is actually simple, I just don't know how to get to it to do the stuff necessary to put a new grub in the offending drive and now there is an added problem due to the size of the drive.  If I do this I will install ubuntu onto a 1tb ssd which will speed up booting.

---

### Post by oldfred on 2022-07-03
May be difficult to go from 2TiB drive to 3TiB drive. 
Default install often is BIOS/MBR to smaller drives and either UEFI/gpt or BIOS/gpt to larger drives.
With gpt you have to have either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.
I have used gpt on all new drives with both BIOS & UEFI systems since 2010, so it works if correct partitions are on drive.

If drive is not seen as first drive in system, and you are installing in UEFI mode, the Ubiquity installer wants to only install grub boot files to ESP on first drive. So is new drive seen as hd0? May be sda, but if you also have NVMe drives they may be first. Drive order is usually set by UEFI/BIOS and then SATA port order. 

So is system UEFI, not familiarwith that motherboard? Are you installing in UEFI? If you have partitions do you have ESP? And then is drive first drive?

Some older Gigabyte issues, may be similar.
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to AMD  boards.

---

### Post by jgw on 2022-07-03
Thanks for the reply!

Question - how old are you? (i'm 87)

Now, I installed ubuntu onto a 1tb ssd, tested the installation, turned off, connected two hard drives (3tb & 4tb) and turned it back on.  It whirred for as long as it took it to install!  Anyway, you aren't going to believe this one.  It came back with all my programs installed, the same photo for the background, etc.  What it did, basically, is reset itself to, almost exactly the same thing!  I have no idea why or how as all the connections got changed, etc.

I'm back in business with this machine!
Well, not really. I have to change addresses in some of the programs.  To do that I have to access the old boot drive.  I can't do that because: "error on mounting: /dev/sdc4 target is busy (udisc-error-quark, 14)" so I have to get around that one.  When it mounted it didn't have a name so i have a very long line of numbers as the name and I have to unmount it to do that.  Must be a way, I will keep on looking.  I was able to change the name of this drive without rebooting but don't know it its working yet.

That drive also has three 1mb boot partition., 1gb empty partition and a really big partition.  

Thanks again!

---

### Post by oldfred on 2022-07-03
You can call me youngfred. I am 11 years younger. :)

I like to label all partitions. I have multiple test installs and data partitions. Then any partition not in fstab, gets mounted with label, unless I mount myself somewhere else. And my external flash drives & external SSD have data partitions with different labels, so I can easily use rsync to copy data.

```
[FONT=monospace][COLOR=#54ff54]**fred@z97-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblkt [/COLOR]
MODEL                      NAME    FSTYPE    SIZE FSUSED LABEL          PARTLABEL MOUNTPOINT                 UUID 
Samsung SSD 840 PRO Series sda             119.2G                                                             
                           &#9500;&#9472;sda1  vfat    499.7M  16.1M                efi       /boot/efi                  F626-A4D4 
                           &#9500;&#9472;sda2              2M                                                             
                           &#9500;&#9472;sda3  ext4     24.4G   7.4G ubuntu         ubuntu    /media/fred/ubuntu         99d27188-274f-469b-aa80-2d06f5d0254d 
                           &#9500;&#9472;sda4  swap      1.9G                                 [SWAP]                     3af6a910-59f8-4719-b58c-2e7484d435f0 
                           &#9500;&#9472;sda5  ext4     10.7G   5.7G iso_ssd        iso_ssd   /media/fred/iso_ssd        695d18b5-16f8-4e9c-bf66-675a12da5a26 
                           &#9500;&#9472;sda6  ext4     24.4G  12.6G focal          focal     /media/fred/focal          db535ec5-b653-4627-9f21-2645e1d7ca4e 
                           &#9492;&#9472;sda7  ext4     28.7G   9.5G jammy          jammy     /                          111c16c5-1cc0-4648-b406-5cd7b38a20ba 
WDC WD10EZEX-00BN5A0       sdb             931.5G                                                             
                           &#9500;&#9472;sdb1  vfat    499.7M        ESP_B          ESP_b                                1640-CADC 
                           &#9500;&#9472;sdb2  ext4     25.4G   7.4G buster         buster    /media/fred/buster         bae2d33a-b56a-4dbb-a631-65cd412dde33 
                           &#9500;&#9472;sdb3  ext4     24.4G   5.8G xenial_b       xenial_b  /media/fred/xenial_b       76dc1759-fff1-419e-85a8-978b35537b0b 
                           &#9500;&#9472;sdb4  ext4    390.6G 121.2G data           data      /mnt/data                  a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 
                           &#9500;&#9472;sdb5  ext4     51.1G  20.9G backup         backup    /media/fred/backup         084de40f-8ffd-4af1-97b1-8a60cdd9aab4 
                           &#9500;&#9472;sdb6  ext4     12.6G   6.9G iso_hdd        iso_hdd   /media/fred/iso_hdd        7f360ddc-d9fb-4a40-b17a-f2d5af6b61ed 
                           &#9500;&#9472;sdb7  swap        2G                                 [SWAP]                     a7750d57-5381-421b-82fa-b53194ab45c2 
                           &#9500;&#9472;sdb8  ext4     25.4G   6.1G impish         impish    /media/fred/impish         c921c627-d6d8-4c6f-affa-f9c12dc6d924 
                           &#9500;&#9472;sdb9  ext4     25.4G     7G kubuntu_b      kubuntu_b /media/fred/kubuntu_b      ab8721c8-5e9a-4075-a762-664e9291005f 
                           &#9500;&#9472;sdb10 ext4     24.4G   8.6G jammy-b        jammy-b   /media/fred/jammy-b        02f05eeb-7957-492d-b7e1-942b2c7fe130 
                           &#9500;&#9472;sdb11 ntfs      9.8G  50.7M ntfs           test      /media/fred/ntfs           455AB22F4596E3ED 
                           &#9500;&#9472;sdb12 ext4     25.4G   9.8G focal_b        focal_b   /media/fred/focal_b        3f6bd30d-5213-4d73-8e90-74473123499c 
                           &#9500;&#9472;sdb13 ext4    156.3G  85.2G photoBU        photoBU   /media/fred/photoBU        f4b155ef-8279-4730-a139-59b50655020c 
                           &#9492;&#9472;sdb14 vfat        6G   3.9G FAT32          test      /media/fred/FAT32          51CD-CC12 
TSSTcorpCD/DVDW SH-S183L   sr0     iso9660 694.7M 694.7M 20030727BACKUP           /media/fred/20030727BACKUP 2003-05-11-13-57-00-00


[/FONT]
```

---

### Post by jgw on 2022-07-03
I got i got the name thing done and fixed.  now I am trying to find stuff and figure out how its doing it.  I use thunderbird for email (for a long time) and want to get on this machine.  I got to their information as to where stuff is but its not s (my machine just froze, be back) where it says it is.  there is only one other place and that is in my old 3tb boot drive and it lied.  VERY strange!  Its just wierd.  My home directory, for instance, has absolutely nothing on it but empty folders.  My boot disk has only about 60gb on it.  I suspect my programs are on it but its a hard find.  I can find the programs themselves but the programs think they are someplace else.  Wierd!

Here is one.  I went to thunderbird and asked it to show me my profile.  It went to files and found it and showed it.  It also showed me the steps.  the steps were /home/greg/thunderbird/  so I stepped it back.  When I pressed the back key it skipped the greg and went directly to /home (no greg)  I then went to files , then to home   home has only one thing in it - something i put there.  Its VERY strange!

Oh, you think you are old now - from now on its life being sneaky and also a bit too educational (you will understand in time)

---

### Post by dragonfly41 on 2022-07-03
> [COLOR=#000000]Oh, you think you are old now - from now on its life being sneaky and also a bit too educational (you will understand in time)[/COLOR]

I am an octogenarian and I don't believe that age matters.
What does matter is making it easier and safer for the older generation to use and apply digital technology.
There was a programme on BBC TV today discussing the Digital Poverty Alliance in U.K.

---

### Post by jgw on 2022-07-03
I could give you a list of the stuff I've got going on.  Between the VA and medicare, however, health is pretty well taken care of.  Currently having dental work done and the blood work is going to end up at about 10/12 grand.  I will goto mexico for the replacing teeth.   I was eating dinner about a month ago, found something hard, pulled it out and it was a 3 tooth bridge.  Thats just the beginning of the tooth stuff.    Then there is the speech aphasia.  There's more but that's the main stuff.  There will also be a lot of minor aches and pains that are pretty much just ignored.  I had a little business and the software  was too expensive so I just did it myself took me a few years but I got it done.  That was when Microsoft just started (I actually got offered a job from I have been retired for years now and I gave the business to my kid and he is still using the programs.    That was when Windows started and I stupidly turned down a job there, used to talk to bill over the phone.  I moved to ubuntu for something to do.  My wife still uses windows and I have forgotten how to deal with it anymore.  Oh, nexxt thursday I get to go to the retina for a 3/4 hour eye thing.   Even with all of that I have made no plans to go real soon. 

Oh, this machine was working just fine and then it did another update and went to hell.  I just tried to install mono and failed with 4 google found how to install places.  I've never had that happen before.  I'm stopping for the day and attack tomorrow. 

Sorry, this has turned into confession time.

---

### Post by oldfred on 2022-07-03
The newest 22.04 has Thunderbird as a snap.

But Thunderbird's profile used to always be in a hidden folder /home/$USER/.thunderbird
But if mounting from a live installer, you will then have the mount you used in addition. Like "/media/fred/focal_b/home/fred/.thunderbird" which is a test install of focal on my sdb drive.

I actually move my thunderbird profile to a folder in my data partition. I started that back in 2006 when using XP and started to use Ubuntu. My wife wanted email & Firefox, so I was rebooting into XP all the time and was having issues learning Ubuntu. So I put the folders in a shared data partition and was able to use from both. Now finding the profiles are more sensitive to version differences.

---

### Post by jgw on 2022-07-05
Thanks for all the help!

I failed to do this and am currently rebuilding my new ssd boot disk.  Its sped up my machine a lot!  And continues to give me pain getting it all set up

---

