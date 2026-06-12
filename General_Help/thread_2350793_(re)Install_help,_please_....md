---
title: "(re)Install help, please ..."
date: 2017-01-27
forum: General Help
---

### Post by Youngblood52 on 2017-01-27
Old Dell C640 laptop originally setup for dual-boot with WinXPPro and Xubuntu 12.10.

When Install is attempted with either 16.04 or 16.04.1 (32bit, on DVDs) all that I get is a text screen that says:

[B]error: file '/boot/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>
[/B]
Which leaves me stuck, as I am a Linux neophyte even after all of these years using it. 

-------[ the rest of the story, short version ]--------

I opted to upgrade the existing Xubuntu installation on my rarely-used laptop (I currently use my dual-booted Win10/Ubuntu Dell Inspiron every day), so I did a regular Distribution Upgrade which took the old laptop to 16.04(.1?).

After the upgrade finished up last evening, I checked out a few things and all seemed to be working OK.

This morning I decided to take it to 16.10.

Most of the way thru installing the packages, it informed me that the upgrade could not be completed and performed an almost instantaneous clean-up and ended the process.

I tried Software Update and the system informed me that it detected a problem that may be the result of a failed Upgrade and tossed me out.

Hmmm ...

I decided to reformat the ext4 part and do a fresh Install of 16.04.1.

No good ... when I startup the laptop and boot from either of the DVDs that I D/Led from Xubuntu.com & burned (16.04 or 16.04.1) I get what I reported at the top of this post.

*Hopefully* there is a simple solution that someone can share ... :)

Thanks!

---

### Post by yancek on 2017-01-27
> After the upgrade finished up last evening, I checked out a few things and all seemed to be working OK.

This morning I decided to take it to 16.10.

That was a mistake.  Are you aware that support for 16.10 ends in 5 months while 16.04 will be supported for over 4 more years.
Are you sure you have the DVD drive set to first boot priority in the BIOS?  I would not expect to see that error booting from a Live DVD.

---

### Post by Youngblood52 on 2017-01-27
> **yancek said:**
> ... Are you sure you have the DVD drive set to first boot priority in the BIOS? ...Yes, it is reading from the DVD drive for BOOT info.

Thanks for the response! :)

---

### Post by mörgæs on 2017-01-28
Xubuntu is not that light any more. For a C640 I recommend Lubuntu 16.04.1 or [Xubuntu Core]("https://xubuntu.org/news/introducing-xubuntu-core/").

If booting from a DVD gives problems then the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") is worth trying.

One plan for the future is to keep 16.04 until support runs out in april 2019, at which time you can do a fresh install of 18.04.

---

### Post by Youngblood52 on 2017-01-28
Thank you, **mörgæs**!

------------------

I found my old Xubuntu 12.10 Install CD, tried it and it started up correctly ... so that told me that laptop components were probably not causing the issue.

I D/Led another copy of the 16.04.01 ISO from another place for use today.

Just in case the DVD Writer is causing the issue, I burned the original ISO to a DVD with *another* drive ... then started up the old Dell laptop with this new DVD ...

... and it worked as it should.  :)

The Install (loaded onto sda2) proceeded without any apparent issue.

Upon restart I was presented with:

[B]error: attempt to read or write outside of disk 'hd0'
Entering rescue mode...
grub rescue>[/B]

So I "successfully" ran **Boot-Repair-Disk**, selecting sda2 (where I loaded Xubuntu) and restarted ... same result.

So I "successfully" *re*-ran **Boot-Repair-Disk** and selected *both* of the presented choices, sda & sda2, and restarted ... same result.

So I "successfully" *re-re*-ran **Boot-Repair-Disk** and selected sda, alone, and restarted ... same result.

<sigh>

BTW, I have my single HDD parted as sda1(WinXP), sda2(Xubuntu), sda5(Linux Swap) and sda6(Share).

Advice for my next logical step to get the Xubuntu 16.04.01 Install to boot?

Thanks, all!

---

### Post by Bashing-om on 2017-01-28
Youngblood52; Hello;

As I pass by :)
As we have :
> 
error: attempt to read or write outside of disk 'hd0'
Entering rescue mode...
grub rescue>

We would be interested in seeing the partitioning on the device.

From the liveDVD booted to "try ubuntu"; key combo ctl+alt+t to gain a terminal interface.
Post back the results - Between Code Tags:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So we see what we have to work toward.

[INDENT][INDENT]gotta be a reason of why
[/INDENT][/INDENT]

---

### Post by Youngblood52 on 2017-01-28
Thank you!  :)

```
xubuntu@xubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.1 GiB, 1227108352 bytes, 2396696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1f831f83

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *           63 209717247 209717185  100G  7 HPFS/NTFS/exFAT
/dev/sda2       209717248 272631807  62914560   30G 83 Linux
/dev/sda3       272631808 312580095  39948288 19.1G  5 Extended
/dev/sda5       272633856 276828159   4194304    2G 82 Linux swap / Solaris
/dev/sda6       276830208 312580095  35749888   17G  b W95 FAT32


xubuntu@xubuntu:~$ 
```



```
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA WDC WD1600BEVE-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  107GB  107GB   primary   ntfs            boot
 2      107GB   140GB  32.2GB  primary   ext4
 3      140GB   160GB  20.5GB  extended
 5      140GB   142GB  2147MB  logical   linux-swap(v1)
 6      142GB   160GB  18.3GB  logical   fat32


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
Ignore/Cancel? Ignore                                                     
Error: Can't have a partition outside the disk!
Ignore/Cancel? Ignore                                                     
Model: HL-DT-ST RW/DVD GCC-4240N (scsi)
Disk /dev/sr0: 1269MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos
Disk Flags: 

Number  Start  End     Size    Type     File system  Flags
 1      131kB  5075MB  5075MB  primary               boot, hidden


xubuntu@xubuntu:~$
```

---

### Post by Bashing-om on 2017-01-29
Youngblood52; Well ...

I have looked at it 3 times, and I do not see the fault in the partition tables .
Must be elsewhere, but above my skill level to isolate. I will also be interested in learning the condition causing the error condition.

[INDENT][INDENT]just not a know it all
[/INDENT][/INDENT]

---

### Post by Youngblood52 on 2017-01-29
Many thanks for taking a run at it, **Bashing-on** ... *and* teaching me about code tags!  :)

Hopefully, someone else who has dealt with this particular issue will wander by.  <fingers crossed>

---

### Post by Youngblood52 on 2017-01-29
I reformatted sda2 and sda5 then rewrote the MBR so that I could start WinXP.

The system is now back to a zero point.

Tomorrow I will re-install Xubuntu 16.04.1 and keep my fingers crossed for the outcome.  :)

---

### Post by Youngblood52 on 2017-01-30
OK ... that worked.

Xubuntu 16.04.1 successfully loaded.  

I set it up as selectable via the windows boot loader and am currently D/Ling & installing updates.

My sincere thanks to all who took the time to peruse the thread and/or offer assistance/advice.  :)

Observation: I had forgotten what a (relative) pig this Dell Latitude is.  Sloooooow even though I have the system cfg maxed. 

It is, however, a bit less slow with Xubuntu.  ;)

---

### Post by Bashing-om on 2017-01-30
Youngblood52l Great !

Pleased you are up and running.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by Youngblood52 on 2017-01-30
Thanks again!

I looked around earlier today for a "[SOLVED]" button and finally decided that it must be done by Mods.

---

### Post by Bashing-om on 2017-01-30
Youngblood52;

;)

---

### Post by Youngblood52 on 2017-02-12
I recently reconfigured two more of my Dell Latitude C640s for dual-boot and installed *Xubuntu 16.04.1 LTS* using that known-good DVD.

The 1st went as it should.

On the 2nd, after generating the .bin, moving it to C:\, reconfiguring C:\boot.ini and trying to reboot into *Xubuntu* I was presented with a black screen + blinking cursor.

After redoing the .bin procedure and experiencing no joy, I ran the *Boot Repair Disk* ... and found myself looking at my weird old friend:


[B]error: attempt to read or write outside of disk 'hd0'
Entering rescue mode...
grub rescue>


[/B]<chuckle> So I repaired & checked the MBR and then repeated the *Xubuntu* Install from scratch, reformatting sda2 to cleanout the 1st Install ...

... and, this time, all worked as it should.  :D

[COLOR=#b22222]**So the Moral of this Thread is (still) that if an *Xubuntu* Install results in such Silliness, nuke it and install it again.**[/COLOR]

---

