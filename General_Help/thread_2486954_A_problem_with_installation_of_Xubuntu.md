---
title: "A problem with installation of Xubuntu"
date: 2023-05-17
forum: General Help
---

### Post by lou6 on 2023-05-17
I recently tried to install Xubuntu.22.04.2 (not my first rodeo, I've been using xubuntu for 10+ years) and ran into some strange problems.  I was being helped by a member and had trouble understanding things he was telling me.  We got nowhere with my installation problem and he stopped responding (hope he's okay, by the way).  I still have not resolved the original problem and hope that a knowledgeable member can help me out.  The thread in question is [Mystery volume on desktop]("https://ubuntuforums.org/showthread.php?t=2486837&p=14142791#post14142791") .  Thank you.

---

### Post by Dennis N on 2023-05-17
In Desktop Settings > Default Icons, have you checked "Removable Devices" and also under that "Disks and Drives"? If so, that selection will pick up other partitions that are not part of your Xubuntu installation.
 
If you unckeck "Disks and Drives" does it go away? That would be one way to get rid of it.

From the other thread (post #5), sda1 is a mounted FAT partition (based on the UUID), but it is not your EFI system partition - that is sda2. Given these facts, I think you could remove sda1 without consequences to Xubuntu by using a partition editor like gparted. It must be unmounted to delete it. It might be some sort of system recovery or diagnostic partition put there by the computer manufacturer. I can't see what's on it, so it's your decision on what to do here. 

Unfortunately, I don't think you can pick and choose which items  get displayed under "Disks and Drives". It's all or none.

---

### Post by TheFu on 2023-05-17
I saw that thread.  I didn't look over it now, so take what I'll write below as general comments, **not specific to your thread.**

Sometimes the solution provided isn't understood or isn't attempted.

Usually when active members stop responding, it is because they don't know any more or believe it is solved or believe no solution exists that will meet with the OP's demands.

Sometimes data is requested, but never provided.  We honestly want to help, not pull teeth. If how to provide the requested data isn't known, ask.  Sometimes is it an easy command. Other times, it is more convoluted.  For example, if I say to "check the SMART data on the disk", that's more complex than just running a single command.

I know very little about xubuntu, so I'm not the right person to address desktop issues, as this seems to be.

---

### Post by lou6 on 2023-05-17
Dennis N - You seem to agree with my thinking - I've moved the phantom icon to the lower right corner of the desktop and as long as the system does everything it should (which it does, so far) why should I care.  The machine I'm using here has been old faithful through 2 or 3 releases of Xubuntu and the machine in question is the one that will be the replacement.  Thanks for replying.

---

### Post by MAFoElffen on 2023-05-18
If you right-click on it, does it have an option in the pop-up menu for properties? If so, in that, does it say the file name and that it resides in the ~/Desktop/ folder?

Xubuntu has a lot of right-click context menu items, where you can add things to the desktop... It might have just been a mis-click that accidentally added to the desktop as a shortcut. I gave you a 3 path's to search for the underlying .desktop file, in your other thread.

---

### Post by yancek on 2023-05-18
Please see my last post in your other thread.  Also, you might try running "sudo fdisk -l"  (without quotes) and posting the output here.

---

### Post by lou6 on 2023-05-18
I tried right-clicking the ghost icon - open and mount are there but properties is grayed out.

if I uncheck removable devices the ghost goes away but then so does a usb drive that I use for backup - I guess I could do that but why?

I ran sudo fdisk -l and got several screens of output but can't see a simple way to get it from that machine to here - let me ponder that...

The thing that nags at me is "why should this install be different from previous installs?"   I can't write it off to a download error - I'm sure there are checksums along the way when I copy to a usb stick.  Oh well... 

Thank you all for your help and suggestions.  Since my new machine is functioning normally (in spite of the mystery icon) I'm going to continue prepping it for future use.  I will try some of the things that have been suggested and post back with any good results.

I'll mark this as solved and start a new post if anything interesting comes up.

---

### Post by MAFoElffen on 2023-05-18
> **lou6 said:**
> I'll mark this as solved and start a new post if anything interesting comes up.
I give up. (LOL)

@lou6 --
(I have to step in and say this...) This is "NOT Solved". You did this with your last thread. Have a little patience before marking something as Solved, just becaue things are not going as fast as you would like them to be.

I recommended that you stick with this to the end, until it is resolved... And that we all understand what is going on. There are a few here that are trying to help you with this, and would like this to be truly solved. We do care, and it does matter to us.

yancek has been helping you. We have been trying to stay out of his way while he does. In the last thread, he noticed that you were getting different output from different instances of your posts. He asked for an update.

I noticed that you hit on something odd that affects it, when you said it went away when: 
> **lou6 said:**
> If I uncheck removable devices the ghost goes away but then so does a usb drive that I use for backup
...and you said the properties option on the right click menu was "grayed out."

That might seems like a small detail, but that actually means something. Uncheck "Removable Devices" where? Is this just a display of your Revable deivices? Like from a temporary mount?

If so, then your USB drive that you use for Backups does not 'go away'... It's still accessible from Thunar, right? It's just not displayed on the Desktop right?

---

### Post by lou6 on 2023-05-18
Perhaps you're right - I may be giving up too easily...

As far as 'yancek has been helping you. We have been trying to stay out of his way  while he does. In the last thread, he noticed that you were getting  different output from different instances of your posts'  I think I confused him by trying to contrast the difference between my 2 computers - they are both running 22.04 but the problem one is 22.04.2 and is giving very different results.  My fault for not being more specific...

The Removable Devices check is from a right click on the desktop.  If I have a usb plugged in it is accessible but if I uncheck Removable Devices the usb is no longer accessible.

Thanks for the encouragement - I've been very busy getting this backup machine ready and part of me just wants it to be over.

---

### Post by yancek on 2023-05-18
> I tried right-clicking the ghost icon - open and mount are there but properties is grayed out.
 

I would not really expect the icon or partition to be accessible for a normal user as it is shown as being on some external device.  That is because of the mount point of  /media/lou/74B2-0187which indicates an external device and a FAT32 filesystem.  Have you tried un mounting it?

```
sudo umount  /media/lou/74B2-0187
```

---

### Post by lou6 on 2023-05-18
@ yancek - 
```
sudo fdisk -l 

Disk /dev/loop0: 63.32 MiB, 66392064 bytes, 129672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 241.9 MiB, 253648896 bytes, 495408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 242.02 MiB, 253779968 bytes, 495664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 349.69 MiB, 366673920 bytes, 716160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 349.69 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 53.24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 53.24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: HGST HTS725050A7
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x7ac960a6

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1          2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2  *    1050624   2101247   1050624   513M ef EFI (FAT-12/16/32)
/dev/sda3       2103294 976771071 974667778 464.8G  5 Extended
/dev/sda5       2103296 976771071 974667776 464.8G 83 Linux

Partition 3 does not start on physical sector boundary.


Disk /dev/loop8: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 63.34 MiB, 66412544 bytes, 129712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

```

sorry - it looks like i truncated the end of loop 9

---

### Post by TheFu on 2023-05-18
All the loop devices aren't real storage.  They are just in the way for this post.  Sadly, I know of no way to get any partitioning tool to exclude loop devices.
It looks to me like only the sda device is real storage.
```
Disk /dev/sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: HGST HTS725050A7
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x7ac960a6

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1          2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2  *    1050624   2101247   1050624   513M ef EFI (FAT-12/16/32)
/dev/sda3       2103294 976771071 974667778 464.8G  5 Extended
/dev/sda5       2103296 976771071 974667776 464.8G 83 Linux

Partition 3 does not start on physical sector boundary.
```
If this is a physical spinning disk, then that last warning aboutnot being on a physical sector boundary can drastically slow the system down (20-30%).  Unfortunately, the fix is not trivial. The easiest answer would be to perform a fresh install and ensure that 4096b boundaries are used for all partitions.  While you are at it, probably best to use GPT partitioning, not MSDOS/MBR partitioning.

---

### Post by #&amp;thj^% on 2023-05-18
> **TheFu said:**
> All the loop devices aren't real storage.  They are just in the way for this post.  Sadly, I know of no way to get any partitioning tool to exclude loop devices.

i'll use this to escape them "all":
```
lsblk | grep -v '^loop'

```

---

### Post by TheFu on 2023-05-18
> **1fallen said:**
> i'll use this to escape them:
```
lsblk | grep -v '^loop'

```

Actually, for **lsblk**, I prefer to use **lsblk -e 7 -o name,size,type,fstype,mountpoint** in an alias.  the ***-e 7*** removes fake storage from the output.

But that doesn't work for **parted**, **fdisk**, **gdisk** partition tools.

---

### Post by lou6 on 2023-05-18
Not that this is germane to anything, but there seem to be larger-than-normal number of folks on Reddit having install problems with ubuntu 22.04.2 -  Probably means nothing but this is the first time I've had a problem with an install since 2012 or so...

---

### Post by lou6 on 2023-05-28
We seem to have reached a dead end in this discussion.  While I have a background in computer programming, my experience was confined to application development on large mainframes and I never understood what went on in the operating systems that ran my programs - therefore, I have no idea what a loop device is (and probably just as well) as far as what I use computers for now.

My current version of Xubuntu (22.04) that I use daily is an online upgrade from 20.04 and has had no problems but the installation I have on my just-in-case-this-one-quits system is the one with the strange icon.  I've tried most everything I can think of on this backup machine and have not found anything that doesn't work but the odd behavior keeps me wondering...

Anyway, I'm willing to wait and see what release 24.04 brings - that's less than a year away and my primary machine could still be humming away until the next upgrade.  If not, then I'll find out if the machine with the odd icon works (or not).

Thanks to all who tried to help - sorry that no resolution was reached.

---

