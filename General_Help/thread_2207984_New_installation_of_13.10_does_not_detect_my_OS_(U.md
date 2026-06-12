---
title: "New installation of 13.10 does not detect my OS (Ubuntu only machine)"
date: 2014-02-26
forum: General Help
---

### Post by Fsirett on 2014-02-26
I really hate to have to come back to this forum again so soon with another problem. but the devil drives...

First of all, I had a collapse of my disk with the original operating system on it, Not a huge surprise since it is well on in years, but I did have anoother (new) disk installed in order to establish the new OS. I divided it into two partitions and began using one and cleared the other some weeks ago. It did have some data on it before, but it has all been erased and formatted.

I installed Ubuntu 13.10 on this partition and booted up and received a no operating system found error.

I then tried again, installing from a newly made live disk, thinking that was the problem, but the same situation.

I have read most of the material on the problem, and I do not have UEFI on my system (I checked and it all comes back "Legacy) 

I used the "something else" option in the installation to select my partition and there have been a few hiccups there, but I did what I have been told ( changed to ext4 and set the mount point to "/" and such. I noticed that with every installation it had reverted to whatever it was before and I thought that odd, but when I changed to what it wanted it seemed to install without any particular problem.

The gparted screen looks like this (sorry, I am still unaware of how to load a screenshot or put my code in the neat box you all do, I am trying the "#" this time, see how that works):

```
ubuntu@ubuntu:~$ sudo parted-l
sudo: parted-l: command not found
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 2      1904MB  476GB   474GB  primary  ext4
 1      476GB   1000GB  524GB  primary  ext4


Model: ATA ST3500320AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext4


Model: ATA WDC WD10EFRX-68J (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 2      1049kB  472GB  472GB  primary  ext4
 1      472GB   982GB  510GB  primary  fat32


Model: WD Elements 10A2 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA ST3500320AS (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  52.7GB  52.7GB  primary   linux-swap(v1)
 2      142GB   500GB   358GB   extended
 7      142GB   490GB   348GB   logical   ext4
 5      490GB   492GB   1347MB  logical   ext4
 6      492GB   500GB   8588MB  logical   linux-swap(v1)
 3      500GB   500GB   1049kB  primary   linux-swap(v1)


Model: ATA ST3250310AS (scsi)
Disk /dev/sdf: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  220GB  220GB   primary   ext4
 2      241GB   250GB  8588MB  extended
 5      241GB   250GB  8588MB  logical   linux-swap(v1)


Error: /dev/sdk: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!    
```

The partition I am using is:

```
Model: ATA ST3500320AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext4
```

I did an fdisk on it as well:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a5d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       929878016  1953523711   511822848   83  Linux
/dev/sda2         3719168   929878015   463079424   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c24f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000bb53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1       922064896  1918687942   498311523+   b  W95 FAT32
/dev/sdc2            2048   922064895   461031424   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a183

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   976707583   488352768    7  HPFS/NTFS/exFAT

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084724

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048   103000063    51499008   82  Linux swap / Solaris
/dev/sde2       276881406   976771071   349944833    5  Extended
/dev/sde3       976771072   976773119        1024   82  Linux swap / Solaris
/dev/sde5       957364224   959995903     1315840   83  Linux
/dev/sde6       959997952   976771071     8386560   82  Linux swap / Solaris
/dev/sde7       276881408   957362175   340240384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048   430120959   215059456   83  Linux
/dev/sdf2       471623678   488396799     8386561    5  Extended
/dev/sdf5       471623680   488396799     8386560   82  Linux swap / Solaris
Note: sector size is 1024 (not 512)

Disk /dev/sdk: 3986 MB, 3986546688 bytes
123 heads, 62 sectors/track, 510 cylinders, total 3893112 sectors
Units = sectors of 1 * 1024 = 1024 bytes
Sector size (logical/physical): 1024 bytes / 1024 bytes
I/O size (minimum/optimal): 1024 bytes / 1024 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   ?   778135908  1919645538  1141509631   72  Unknown
/dev/sdk2   ?   168689522  2104717761  1936028240   65  Novell Netware 386
/dev/sdk3   ?  1869881465  3805909656  1936028192   79  Unknown
/dev/sdk4   ?  2885681152  2885736650       55499    d  Unknown

Partition table entries are not in disk order
```


The part that applies to my partition is this:

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000bb53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1       922064896  1918687942   498311523+   b  W95 FAT32
/dev/sdc2            2048   922064895   461031424   83  Linux

Partition table entries are not in disk order
```


I am using /dev/sdc1 as the operating system partition. 

I know the partition is large, but I originally had it divided in two parts. I was going to separate the system from the /home files but when the problem occurred I thought that it might be better with a larger partition; apparently, not on my watch.

I can find no copy of my problem. They all seem to have something to do with problems in a dual boot situation and most come down to some sort of UEFI problem, it would seem

I know I am being abit of a pain, but  with all these problems, but I should get credit for persistence. I am persistently screwing up Ubuntu! I was much more able (at screwing up) with XP, if that is any comfort

Frank Sirett

---

### Post by squakie on 2014-02-26
I don't know what you may have done - did you burn the LiveCD as an image, not just burning the files to it?  Was your BIOS set (or did you use some function key at boot) to set the boot order to look at the livecd first?

For your current install of 13.10, when you did the "other" did you look at the bottom of the screen to see where it was installing the grub boot loader?  

You show sdb and sdc in your post - what is sda?  Does it have another operating system on it?  Do you want to be able to boot it or Ubuntu (called dual-booting)?


What would probably help is to get the report from boot repair as to how your system is set up.  You can download and burn the boot-repair CD and then boot from it.  Be sure to check the net or post back here if you need help.  For now, don't let it update anything.  Post back the link it gives for where it posted the report.

---

### Post by Fsirett on 2014-02-26
Cheers tio that. I will go ahead a little later and use the boot repair disk. I am using a live cd at the moment and I want to get what I can down as soon as possible - Hopefully waste less of your time.

Sda is a disk I use for data alone. It has never had an operating system on it and never will. very odd that it never turned up, it has two partitins that I can access; at least they turn up on the files screen.

As to the grub boot loader, it never occurred to me to look or check there. I have never had a problem with it in the past. That said, it is now going on the list. I might be dumb, but I am not stupid. Cheers for the heads up on that.

I am not using a dual boot at all. My entire system is running Ubuntu and has been for quite some time. This is the first time this has ever occurred. I am certain I have done something dumb (or stupid) along the way. 

With this newest live cd running all of the partition numbers have changed, but the actual disk is: ATA WDC WD10EARS-00Y, if that is of any help.

I have a boot repair disk, possibly a little old, I think I made it for Ubuntu 12, but I will try that and send you the results. That might be an hour or so from now, I have some work that has to get done and I have to go out for few minutes. 

In any case cheers for the help so far!

Frank Sirett

PS: I burned the disks as an image in every case. For the USB that I used, I burned that on my wife's Windows 7 computer using the suggested USB boot creator, but I am using the latest Ubuntu disk at the moment. I did burn it from this system using the USB that I do not completely trust. Could that be a problem? It seems to work well, but the Boot programme did not work the first time at it. Hence I made another disk to be certain.

F S

---

### Post by Fsirett on 2014-02-26
I opened with the Boot recovery disk and brought down the report

I have removed that endless list of text (as suggested) and this is the link to [the report]("http://paste.ubuntu,com/6999912/") 

I am not completely clear on all of the details, as in not very clear at all, but ...am I mistaken in thinking the system was actually installed on a completely different drive? Still does exactly the same thing, but it looks like one of the drives I had has been wiped and something new put on. Not important, since it was the electronic equivalent of a junk box, but I wonder if I specified the wrong drive. I still see something on the targetted drive, so maybe I did it twice?

I am looking for a permanent solution to this problem, but I would rather put the OS on the partition of the new drive since the 500G drive has been well used and is in line to be the next to fail

Cheers,

Frank Sirett

---

### Post by squakie on 2014-02-26
Just post the link to the report - boot-repair will give you a net address so we can look at it.  Also, please enclose data replies inside the <code></code> tags - you can do this by clicking the # sign on the reply edior menu - if you don't see it then select "Go Advanced".  Once those 2 tags are showing, paste your output (or type it in) between the 2 tags - e.g., between the ">" and the "<" seperating the 2 tags.

Okay, which hard disk is your BIOS set to boot from?

---

### Post by Fsirett on 2014-02-26
Yes, I can see that would have been a much better idea. I have no idea where that long list of line numbers came from, they do not appear on the original I have here. I think I might go in and edit out the stuff and add in the link for future readers. I assume the posts are archived. 

I also thought I had used the (newly discovered by me) "#" tags, but apparently not. Sorry about this. 

First of all, the 200Gb disk is the one that failed. An old soldier to be sure. Well used and deserving of its rest.

I am trying to put it into the FAT32 partition, That being sdc1 or UUID 9B30-6E9C on this sheet. There might be some odd things going on, if you might do me the great favour of clearing up a few questions I have.

First, although I am not really certain, does the report say I have three instances of Grub 2? If so, does this mean there were at least two instances of Ubuntu trying to install , one of them being in the place I was not wanting it to?

Second, I see a drive with an EFI notation. I read that this was something I had access to on the Bios and, since my BIOS gave no sign, i believed I could not have. I ran a suggested script to check and it came back "legacy" and so I assumed that was the situation.

Last of all, at least I hope this is last of all, is there a good reference that can explain how to use the installer's more esoteric elements so I can avoid the problems in the future.

I have been thinking about it, and I seem to remember it was about Ubuntu 11 that I began to have problems but just upgraded without doing a clean reinstall. I remember those Windows days and putting off the inevitable for as long as possible because of the time it took to get back up and running. I should (approval wanted) actually do a clean reinstall with every major upgrade. I strongly suspect this has been the reason for many of my misfortunes. Errors cascading into disasters. 

However, no real knowledge leaves me doing what appears to be the right and logical thing (compounded by doing exactly what people suggest from all sorts of online sources) and end up doing something stupid, like installing multiple versions of the OS when I think I am doing exactly what I am supposed to do. 

When people say I am a "know-nothing," my only answer is "I don't know about that"

Cheers again,

Frank Sirett

---

### Post by squakie on 2014-02-27
PLEASE:  read this entire post 2 or 3 times before you start.  If you have any questions ask them first before doing anything.

The only thing I can see worrying about right now is actually getting it installed so you can boot Ubuntu.  With no other OS on the system this *should* be easy enough.

I'm assuming the following:

- you want a clean install of the OS so you can boot it
- whatever device you are going to use has no data you want to keep - if this is not the case STOP here and post back
- you want Ubuntu on sdb - if not, select the device you want (sda, sdb, sdc, etc.)
- when you say you want it in the FAT32 partition, I'm assuming you DON'T mean Ubuntu - you can't install it there, it must be in an acceptable linux partition.
- you ONLY want to boot Ubuntu

That being said, start the installer.  When you get to the disk selection menu select "Other" and select /dev/sdb (or the device you have selected for Ubuntu) . Since you never got this booting I assume you have no data there.  Remove the existing ext4 partition you want to replace with Ubuntu (I don't see swap anywhere, just ext4). Now add 1 partition for swap.  The size is dependant on a couple of things:

- if you plan to hibernate, you'll need the size to be about twice the size of your physical memory plus a little overhead

- if you don't plan to hibernate, consider you main memory: if less than 2GB, I'd make the swap about 4GB.  If greater than 2GB, I would make the swap about 2GB.  That's just me - others will have other opinions on that, none of which are really wrong.

Now, create a partition in the rest of the free space, make it ext4, and make the mount point "/".

Now look down at the bottom - it shows where it will install grub.  In your case  you would want this to be /dev/sdb or whatever the device was you selected.

Continue with the install.

When finished, be sure you BIOS boot order is set correctly:

- if you have a choice for USB, make it first or second
- make your optical media drive first or second
- male the drive that is sdb (or whatever device you installed to) third
- no other optiions should be needed that I can think of at this time.

Hopefully this will get a new bootable installation and your system will boot Ubuntu.  Please post back the result.

After we get a new bootable installation running, we can try to address you other questions/problems.  Please note that I am not 1 of the big experts here - I'm just a guy trying help.  If you are confused by any of what I have suggested or you think it may be wrong, please post back and don't attempt the install.

I'm taking you at your word this is NOT a EFI or UEFI system.  Things might need to be a little different it is.  I'm not very familiar with that so I don't know if there is anything that needs to be different or not.


Also - if this a 64-bit machine use the 64-bit Ubuntu iso.  It will work with EFI/UEFI and legacy whereas I don't know if the 32-bit will.

Hopefully someone else will see this and review it and suggest any changes, etc., in case I've made an error somewhere.

---

### Post by Fsirett on 2014-02-27
Cheers again! I really appreciate this. 

If I am correct, it looks like the main problem I had was not tending to the location of the grub installation. Nothing I saw on the net mentioned that as a concern.

Let me explain for you, and possibly others who may follow. The partition was formated as FAT32 because some article somewhere or other told me this was part of the cure for the problem. The original format was Ubuntu. I love to read, but what I read is not always something I should act on. 

I have loads of Ram, in fact I have it topped right up to the maximum - 8GB, so I will load a 4Gb swap just to be safe. Why not? I will be replacing he 250 drive with as large as is reliable, once again, just to be safe

I was wondering about the boot order in the bios myself. I changed it a few times to see if that helped...it did not...but I was on my own there. I saw no posts mentioning boot order and I thought I might have been on the wrong track so I put it all back to the way it was, starting with the crashed drive. I am a dab hand at taking a small problem and turning it into a proper disaster so I am always second guessing my instincts. I do not buy snake oil and such, but I do fall prey to bad advice on the internet that has to do with the computer...mostly. I am sceptical by nature and habit but I am quite vulnerable when it comes to computer problems that I would be best off leaving alone until I get reliable information. I think my epitaph is going to read "I did not think it worth bothering you with so I looked up my own solution. FYI peachpits do not cure cancer"

I will do all of this and be back with a report in a few hours!

Frank Sirett

---

### Post by Fsirett on 2014-02-27
The good news is that I am now on a proper system. I really want to thank you for that.

The system did not want to boot up when I began, and so I went to the Boot Recovery disk and let it do its thing. All seems to be working from where it is supposed to be working and the report is here:

[paste.ubuntu.com/7006550/]("http://paste.ubuntu.com/7006550/")

I have every intention of moving the /home folder to another disk to make things easier n the future. I was thinking of using the instructions from:
[URL="http://www.maketecheasier.com/move-home-folder-ubuntu/"]
http://www.maketecheasier.com/move-home-folder-ubuntu/[/URL]

But i would certainly appreciate any advice on the quality of this advice. It is my thought that I should be renewing the installation much more frequently and I believe the problems come, at least in part, from legacy problems that were not solved and were retained during upgrades. 

I then intend on recovering the old /home folder from the failed disk and merge that into the new version so I can save myself the problems of that which had not been backed up.

All this seems logical to me, but may not be the best idea. I am interested in your advice.

Of course I am now left with all sorts of debris on the system that has to be cleaned up and that I believe you alluded to earlier. 

Hopefully this will cure no end of problems in the future. It would appear I am in need of such medicine. I seem to be having trouble distinguishing between these ends and holes in the ground.

By the way, did you know cats and dos, most pets, really, dislike mysteries? They just do not like the twist in the tail.

Cheers 

Frank Sirett

PS now I am looking at the system, I notice that drives are disappearing on me and appearing again. I updated everything and restarted the computer and now I see some of my older drives have diasappeared and ones I thought were dead have reappeared. I think this might have something different. It could be loose cables, but it could be something else. Any ideas?

F. S.

---

### Post by squakie on 2014-02-27
I'm really not familiar with moving the /home folders around, sorry about that.  I know it can be done, and what I've read on the forums it seems to be fairly easy.  I would advise opeing another thread just for that single issue.

As far as the disks appearing and disapearing, I don't know.  When they disapear can you start gparted and see if they are at least showing there under devices?  If you don't have gparted:

sudo apt-get install gparted <press enter>

To run:

sudo gparted <press enter>

Be careful not to make any changes there unless you really want to!!   Really not knowing, I suspect you would use it to create a new partition somewhere you want as your new /home, and then somehow change the "pointer" to /home - perhaps by defining a link.  But I'll leave that to someone who really knows.  If you do open a seperate thread for that issue at least you should be getting current information instead of possibly outdated information.

You may also want to start a seperate thread just on your disks issue as well.  Keeping things in seperate threads will get you the most help on any given issue, and is sort of a unspoken rule in the forums.  I'd post those in the absolute beginners forum - they will get more exposure, and a moderator will move them to another forum if they deem it neccessary.

Like I said, I'm really no expert.  If I was able to help in some way so far all is good.  I thought just doing a new install and watching the location of the grub loader and where the BIOS said to boot from would help, but you never know.

I would suggest closing this thread since you now have a bootable system, and use new threads for your other questions.  Ask as much as  you want - that's why the forums are there.  They are a great resource and I get more up-to-date info there compared to reading potentially outdated info on the net.  So much changes so quickly that what was correct 3 months ago may not be today ;)

I'll watch for your other threads and *if* I can help I'll try.  I'm just glad you have things figured out and have a booting system again - that's the first big step out of the way!  ;) ;)

Dave

EDIT:  I also just remembered - if you don't have the package manager installed already I would suggest:

sudo apt-get install synaptic <press enter>

Then the synaptic package manager will be available so you can view/select/install/remove things GREATLY easier than using the command interface to apt.  For some reason synaptic wasn't installed by default in my 13.04 and 13.10 installations.  If you don't know, synaptic package manager is a GUI'd "menu'd" interface - makes life much easier.  After installation it will be in the Unity menus.

---

### Post by Fsirett on 2014-02-27
Cheers again!

I more than a little suspect the drive problem is either a loose cable or some configuration problem. They are appearing and disappearing rather oddly. Right now my failed drive is beginning to appear and it wants me to believe it is hale and hearty. I do not trust it. The other drive that s disappearing is also old and overused so I might just be having some bad luck. I will think about that a while before I bother anybody with it. I will look at the connections in the morning and have another think if it starts to act funny again. The (now) missing drive was subsumed by another file a while ago (no idea why or how) and became unreadable save through that file. It took an age too find it, but I did eventually. 

I use gparted quite a lot. Not to handle partitions much but to keep an eye on what I am doing and to get an idea of what is going on where. I have a full house of disks and it is nice to know what is where when the disks begin to age. More for housekeeping than anything else, but when I do need to do something real, it is there for me to use...or misuse.

I think your advice to get up to date information is a wise suggestion. I suspect I have been looking at material that is well out of date and that has been leading me astray...then I am toast and the "astray" turns into an "ashtray?"

I did once have the synaptic package manager, but I think it came standard on an older version of Ubuntu. Having come from a Windows syatem, Ubuntu is like a toy shop for me. Lots of stuff to help me break everything, but in this case there are people to help and I can learn all sorts of things, like looking to see where the booting files are put. Logical on the outside, but sticky and with nuts when you get into it. distance and experience offer much better views.

As i say, cheers for that. Nothing is really of tremendous importance since I now have to shop for a new diskamd I suspect I will partition a large slice of that for my new /home. It just strikes me as more convenient than worrying about having backed it up when there is a problem and a quick, clean reinstall might make more sense. I am now just wondering if SATA cables break down? I have a history with cables. Some may use them to throttle, but I want to actually throttle them quite frequently. I must think about them. It couldn't hurt much if I simply replace them and that might be the problem!

I digress. Thanks again. Big help, really appreciate it!

Frank Sirett

---

### Post by squakie on 2014-02-27
I'd check your power supply - it's possible it may be going flaky on you.

---

