---
title: "Linux partitioning"
date: 2008-06-13
forum: General Help
---

### Post by ktechman on 2008-06-13
Moderator is there any way to put this guide up as a sticky?

> Guide to Partitioning for Linux

In this guide I will take you through some of the tings you need to know when preparing a hard drive for Linux. Some of these things relate to performance, some to security. The first thing you shoudl do before doing any hard drive work is to BACK UP ALL OF YOUR DATA. You've been warned.

Next thing to do is grab a pad and paper and something to drink (non-alcoholic as alcohol and partitioning doesn't mix) Partitioning is one of the lost arts of computer tuning. Let me give you some background on my experience.

First I have been able to load over 15 operating systems on the same hard drive before, all accessible from either the windows or the linux boot managers. I have used programs like partition magic and such but I find that using the FDISK utility that comes with each operating system is just as effective and in mose cases makes for far more stable a system. I have been workign with hard drive geometry for over five years and during that time I have learned quite a few things. The first thing to learn is that you must do everythign on paper first. "Proper Prior Planning Prevents Piss Poor Performance" as my ex-wife's father used to say.... brilliant man.

Now if you're all set we can begin. I can;t use ascii for this since the page doesn't parse spaces correctly.(hey admin... can you make a feature that lets us draw directly into posts?)

Step One: Visualize

Draw a rectangle about the width of the page about an inch high.

Now you have the form with which to begin molding your new drive partition system. If you have multiple drives draw boxes for them too. Don't worry about proportions as this is just to visualize what you are doing.

Step Two: Positional Planning and Taking Stock

Within the box you will need to divide it into separate compartments. Each of these will represent the partition you are creating and will list what types of partitions you are creating. Before you begin slashing up this space you have to plan for what you will be installing. Some people have Windows and Lin ux dual booted, some just use single OS's with removable hard drive kits, still others install many operating systems. This guide will focus on a Windows/Linux Dual boot configuration. If you are just doing one or the other you can refer to the charts at the end of the guide to help you determine what you need to do after reading this guide.

Hard drives work by spinning a disk and moving several arms across the surface to read and write from the surface of the disk. When your computer is off the arms are stowed away off of the surface of the disk. When it boots up the arms move to the edge of the disk and begin reading the first track at the edge... this track 0 and is also known as the MBR. Each track is divided into sectors and again into blocks. The important thing to remember is that like a record player the arm reads data from the outside in. the majority of the time a hard drive spends looking for data is in the process of moving the arm to the appropriate track. If you want to increase system performance you need to do whatever you can to limit the amount of real estate that arm needs to cover to get to any given information.... virtual memory and linux swap spaces included. The system hits these constantly and as such you can find the arm constantly swinging back and forth across the disk surface... causing massive time loss in the long run. The solution is to place these areas of the hard drive as close to the core operating system as possible. In the old days space was limited so this was never a problem. Even today if you have a drive of less than 20 gigs you don;t need to worry about it as you don;t have the real estate to do anything about it. Now with hard drives fast approaching a half a terrabyte... you have the room to tweak this often forgotten aspect.

Now we'll say for the sample of this guide you have a 100 gigabyte drive. The first thing you need to do is take an inventory of all of the software you plan to install. All of your games, all of your applications... for me that's less than 30 gigabytes. This will be your windows partition. Don;t figure in your music or photo collections or any other personal data... we'll get to that later. Just the amount of data space you need for all of your applications. IF you got the number add 10% to whatever it is and round it up to the nearest increment of 5. In my case I figure I needed 30 gigabytes... add the 10% to make it 33 gigs and then rounded up to a nice even 35 gigabytes. Go ahead and draw a line at about that point on your bar. Write in Windows and 35gb in the box (leave some room for additional info as we get to it)

Now we need to separate the windows virtual memory system from the system partition. If you have the luxury of a second hard drive you can put it on there but for now we'll assume you don't. This partition only needs to be a maximum of 2 gigabytes... draw a sliver in the space next to the first box and label it as the windows VM 2gb. You have already started to amplify the speed of your hard drive by more than 50% by cutting out half of the drive you need to search to find anything. That covers windows with 2 partitions, but what about linux?

For linux we need to set up many partitions.. most will be small and will b e located within an extended partition. Windows has to be in a primary partition and so does linux's /boot filesystem. This isn't a problem as we have one primary left to work with. out of the 100 gigabytes we have about 63 left to play with. Linux in total will need no more than 5 gigabytes, 10 if you plan to go wild with many applications. It's no where's near the "bloatware" that windows applications are. The first partition you will need to plan for is the core of the linux OS... the Root. All things come form root and everything in linux.. even hardware... is a file inside of root. It truly is a very zen operating system in this respect. You will need about 4 gigabytes for the root file system... more if you really plan to do some heavy work. I use 10 to be on the safe side. Add in this space to your bar and label it linux root 10gb. Now we only have one more partition left we can actually make as a primary, but several left to make. The rest of the drive will be an extended partition. Write that in and draw a new bar to represent that space. In this example I have 53 gigabytes left of real estate in the extended partiton. For logical dives we will need a swap drive, a temp drive a variable drive, a home drive, and a place to save files from both windows and linux. As with windows you will only ever need 2 gigs of swap space so draw that sliver in first. label it accordingly as a Linux Swap 2gb. The Linux swap is similar to the windows Virtual memory page file in that it's a place for the system to store data that is in the middle of being processed but cannot fit into main memory. Unlike Windows however Linux MUST have a swap space. It is a requirement for the system to even operate, even if you have enough memory for the system to never use it. Now that we have the root and swap planned out let's begin with the rest.

The temporary and Variable /tmp and /var paths in linux respectively are separate for security reasons. These locations are publicly writeable and having them in with the rest of the operating system can cause a denial of service attack. Additionally any user can write to their home directory so you also want that separate from the rest of the root filesystem as possible. If the root filesystem's partiton shoudl ever become completely full the system will crash and most likely be lost. Keeping these areas separate will save you alot of headache in the long run and is much safer than simply setting software disk quotas. Temp can be as small as as 500 megabytes but I like to give some breathing room for large applications to write to so I use 5 gigabytes for both of the /tmp and /var filesystems. This will only bring our total remaining to 41 so it's not a big hit at all. If you plan on running a web server or FTP server the files will be stored in /var... along with system logs and such. If you plan on accessing and using these features then give it some more room as you see fit. draw and label those partitions in accordingly. when you are done you only have the /home area and the shared areas left. if you plan on transferring alot of files between the two systems then make the shared area larger. If you plan to do most of your wirk in Linux and don't need a large area... make the home area bigger. I tend to allow 10 gigs for home and the rest to shared. this leaves us with a 31 gigabyte partiton to make into a shared space. For the sake of simplicity I make the home a little bigger to bring the shared space under the 30 gigabyte FAT32 limit. Linux has a history of disliking NTFS so it should be avoided whenever possible.

Step 3: Partiton Away

Now that the plan is settled go ahead and create your first two partitons using The windows setup and get that OS installed. Once the system is installed you can refer to my guide on windows virtual memory to move it to the second partion. For simplicity you may wish to hide this partiton in windows by using the drive manager to assign no drive letter or path to it. This will effectively remove it from 2000/2003/XP's my computer and prevent you from accidentlaly writing to it. Once that's done it's on to linux.

Once you start up the linux installer you will be bombarded with a bunch of stuff that is difficult to understand at first. There are plenty of how-to's on the net on using the linux FDisk program or the partition manager that comes in such distributions as red hat or whatnot. Just avoid changing the first two partitions and go through creating your other partitions. Most linux installers will give you the option of installing certain filesystems to certain partitions. Go ahead and do that when you are prompted. If no option is given then you may have to do it manually, which is beyond the scope of this guide. Finish the linux install, and set up windows in the linux Boot manager.(usually grub or lilo) There are also how-to's on settign this up available in almost every linux distro's help files. When you get back into windows start up the drive manager and add in the shared partition into the remaining unallocated space at the end of the extended partition. If it shows the whole thing as unallocated you will have to exit there and do it from the linux FDisk. Either way make this partiton Fat 32 and add it to the linux FSTAB file (once again there are how-to's on this on the net)

That's it. Below I will detail showing some different setups for different situations that work for me. If the system is a solo linux system it will also include a /boot to keep the boot files separate. I'll use percentages of total disk space to denote the sizes of the partitions. Note that there are minimums for each area of linux and you may have to adjust your partition sizes accordingly. It's not an exact science so feel free to experiment.

Format:
Partiton Type - Useage - Filesystem - Approx. Size

Windows / Linux dual boot
-------------------------

PRIMARY - Windows - NTFS - 30%
PRIMARY - Windows Paging - NTFS - 2%
PRIMARY - Linux / - EXT3 - 10%
EXTENDED
LOGICAL - Linux Swap - Linux SWAP - 2%
LOGICAL - Linux /TMP - EXT3 - 5%
LOGICAL - Linux /VAR - EXT3 - 5%
LOGICAL - Linux /HOME - EXT3 - 26%
LOGICAL - WIN/LIN Shared - FAT32 - 30%

Linux Solo System
-----------------

PRIMARY - Linux /Boot - EXT3 - 2% (200mb is fine)
PRIMARY - Linux / - EXT3 - 10% (3gb minimum in most cases)
PRIMARY - Linux SWAP - Linux SWAP - 2%
EXTENDED
LOGICAL - Linux /TMP - EXT3 - 5%
LOGICAL - Linux /VAR - EXT3 - 10%
LOGICAL - Linux /HOME - EXT3 - 71%

Windows / Linux Dual boot.. Multiple Hard Drives
----------------------------------------------

Hard Drive 1 (/dev/hda for linux IDE drives)

PRIMARY - Windows - NTFS - 50%
PRIMARY - Linux / - EXT3 - 48%
PRIMARY - Linux SWAP - Linux SWAP - 2%

Hard Drive 2 (/dev/hdb for linux IDE drives)

PRIMARY - Windows Paging - NTFS 2%
PRIMARY - Linux SWAP - Linux SWAP - 2%
PRIMARY - WIN/LIN Shared - FAT32 - 30%
EXTENDED
LOGICAL - Linux /TMP - 5%
LOGICAL - Linux /VAR - 10%
LOGICAL - Linux /HOME - 51%

(note: While more than one space for virtual memory can improve windows performance it isn't usually worth it. On the other hand having 2 linux swap spaces on separate drives will greatly enhance the efficiency of the system.)

Once again these are general IDEAS and you can customize these to suit whatever needs you have. There is no magical scheme that will work for everyone... this is only a guide to get you going on discovering what works for you.

I hope this guide helps you plan your system and helps you understand that software plannign is just as important as hardware planning.
__________________
Linux is ZEN
---------------------------------------------------

Never underestimate the power of the DORK side. By: Kittani on overclockers.net

Regards

---

### Post by confused57 on 2008-06-13
Also, this partitioning guide may help:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by ktechman on 2008-06-13
I like the reasoning here, if I would have had these two resources when I first started it would have made my start go somewhat smoother. In my opinion, there should be a must read list before you start for the first time with Ubuntu. Thoughts?

Regards

---

### Post by Ender305 on 2008-06-13
It isn't necessary for the root filesystem in linux to be in a primary partition, I have an ubuntu installation on an extended partition that works fine

---

### Post by ktechman on 2008-06-13
Ender, why the debate it will only confuse the issue at hand which is a complete comprehensive guide of the subject of partitioning for the newcomer.

Regards

---

### Post by Gonzalo_VC on 2008-06-13
[COLOR="Navy"]Hi, pals!
I deleted a Ubuntu distro from my laptop because I was going to change the partitions (enlarge the "\" )to install a new one. 
But now the laptop does not reboot, because grub is still there and  I can't modify the partitions from the live-CD of Ubuntu.

Neither can boot the laptop with a WindowsXP CD because it ask me for a drive A (diskette) that it doesn't have. 

How can I format the MBR from a live-CD of Linu!!?? :(
THANKS![/COLOR]

---

### Post by VMC on 2008-06-14
> **Gonzalo_VC said:**
> [COLOR="Navy"]Hi, pals!
I deleted a Ubuntu distro from my laptop because I was going to change the partitions (enlarge the "\" )to install a new one. 
But now the laptop does not reboot, because grub is still there and  I can't modify the partitions from the live-CD of Ubuntu.

Neither can boot the laptop with a WindowsXP CD because it ask me for a drive A (diskette) that it doesn't have. 

How can I format the MBR from a live-CD of Linu!!?? :(
THANKS![/COLOR]

Download Super Grub. Its a livecd. Then follow this :[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page) instructions

---

### Post by jrusso2 on 2008-06-14
> **ktechman said:**
> Ender, why the debate it will only confuse the issue at hand which is a complete comprehensive guide of the subject of partitioning for the newcomer.

Regards

Because they might be short of partitions unless they use an extended if they are dual booting

---

### Post by VMC on 2008-06-14
> **jrusso2 said:**
> Because they might be short of partitions unless they use an extended if they are dual booting

Also I don't think he's debating the subject but adding to it. It makes a more complete guide if the user has all the options available to use. Or wasn't aware he could use extended partitions.

---

### Post by Gonzalo_VC on 2008-06-15
> **VMC said:**
> Download Super Grub. Its a livecd. Then follow this :[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page) instructions

[COLOR="Navy"]THANKS!

I worked hours and managed to delete all the partitions and re-create them (different sizes). Then I installed the new **Poseidon 3.0** (an "academic Linux" based on Ubuntu) and it installed grub again, so I can dual-boot again, normally and everyone is happy :)[/COLOR]

---

