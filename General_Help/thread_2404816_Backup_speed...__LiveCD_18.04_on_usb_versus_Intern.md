---
title: "Backup speed...  LiveCD 18.04 on usb versus Internal SSD boot etc."
date: 2018-10-28
forum: General Help
---

### Post by starlightflyby on 2018-10-28
Hi.   I am emerging from a 3 day unplanned upgrade from Ubuntu 16.04 LTS to 18.04.1 LTS on a Dell laptop, Precision 7510.    

The upgrade was triggered by suddenly getting stuck in the lightdm login loop.  Thanks to many forum posts, I found my way to the Shift Ctrl F1 terminal windows, which worked.  As I had been seeing the invites to upgrade to 18, I decided to go that way rather than try to fix Ubuntu 16.

During the process,  I noticed extreme differences in backup speeds and am really curious whether I did something fundamentally wrong or should have expected the differences.  I will give some details below.

I do not know what to call the type of Terminal opened with Shift Ctrl F1.  Do those terminal sessions have access to less CPU or RAM than if lightdm had let me in and let me run a terminal?  I will call those Shift Terminals just in case that matters.

My laptop has an SSD drive which boots Ubuntu.  It also has a second 2TB drive for extra storage and I do not recall exactly, but I think it is hybrid ssd.  I will call that the hybrid drive.  That drive is partitioned with 1.3TB and 500 GB.    For backup target,   I used various Seagate backup drives over usb.  Those external disks all support usb 3.0, with blue edges inside the usb connector of the cable.  Afaik all ports on this Dell support usb 3.0.  I tried different ports and diff disks, up to 2 yrs old to brand new; that made little difference.

The fastest speed reported was 9 gig per minute.  The slowest was just a few hundred MB in 15minutes.    The most common was about 0.85 Gig per minute average.  All the rsync tests started faster and then slowed down.

As I had more than 2 TB to backup, these were critical speed differences.

All usb disks had NTFS format.

Ok now the scenarios.

1.  Shift Terminal on v16.04
rsync of data from the hybrid drive to usb external
0.85 Gig per minute

I tried cp instead of rsync and it might have been a bit faster  but I was not convinced it could restart and capture every important difference.   

I tried using multiple shift terminals to copy different directories to the same disk, or to  target different usb disks in parallel.  Trying to do more over usb in parallel turned out to be extra bad.  Shutdown became super super slow. Often had to power off via hardware power button.

2.   CloneZilla booted from an external usb flash drive made with YUMI.  YUMI was a wonderful discovery btw.     

9 gig per minute when backing up the entire internal ssd  disk

5 gig per minute when backing up partitions of the hybrid disk.

3.   Ubuntu 18.04 booted from LiveCD on flash usb under YUMI
( And it was a huge relief to see all my data and have a working system with LiveCD. So grateful for that.)

Normal terminal prompt within 18.04 live

rsync  of my 16.04     /usr/*  files  to external usb
So slow.   I waited an hour and far less than 1 gb had copied.  Had to interrupt it.


Bottom line.  Why couldn't rsync  run at 5 or 9 gb per minute ?  Does it need to be so much slower in order to stay aware of files vs the disk blocks that clonezilla works with?   Why was rsync  done from the LiveCD boot so so so slow ?    Was YUMI part of the slowdown ?

Thank you.

---

### Post by TheFu on 2018-10-29
NTFS drivers don't use the big_writes option by default, so performance is limited to 4K blocks.  If you can't change from NTFS to a Linux file system, then using that mount option will help. From the mount.ntfs manpage:
```
       big_writes
              This option prevents fuse from splitting write buffers  into  4K
              chunks,  enabling  big  write buffers to be transferred from the
              application in a single step (up to some system limit, generally
              128K bytes).
```

Many people use the GUI to mount external storage.  That uses GVFS which is known to be slow.  If you use a *real* mount, defined as a mount that shows up in the mtab file (GVFS doesn't), then performance will vastly improve.   To achieve this, there are 3 methods:
* /etc/fstab config
* autofs setup
* manually typing/scripting a **mount** command.

 The NTFS driver is FUSE, which will **always** be slower than a kernel-based driver. Always. 

In general, backups using rsync to NTFS will lose owner, group, permissions, and ACLs. On a multi-user OS, that is a total failure in a backup.  But if you are only backing up 1 userid's HOME, then the owner and group might be sufficient.  If you are backing up other parts of the OS, NTFS is nowhere near sufficient.

BTW, rather than using per-minute numbers, if you can please stay with Mbps, that would be helpful.  Nobody in networking or disk performance think in any other units.  mega-bits-per-second.  Not GB/min, not MBps (Mega-bytes-per-second) either.  It would be easier to parse if you listed the total size of the back and elapsed time, if using Mbps isn't possible.

I'm a backup and disaster recovery person.  It was a huge part of my professional career. My suggestions:
* switch from NTFS to almost any Linux-based file system (ext4, zfs, xfs)
* avoid using gvfs
* I've been burned by Seagate storage a few times. For very large drives, they appear to have engineered the problems out (10TB and larger) and some of their really old drives (600G and smaller) were fantastic devices.  750G - 6TB devices can only be described as "caution needed".
* USB3 is fine for backup connected storage where there's effectively 1-2 queued storage commands.  Running an OS off USB2/3 brings in queuing issues that the USB storage command set doesn't handle well. In a pinch, it is serviceable, but should be avoided. Primary storage should be SATA, SAS, eSATA connected or one of the new-fangled NVMe storage devices.

IMHO.

---

### Post by starlightflyby on 2018-10-30
@TheFu   Thank you very much for your HO!  It seems very well grounded. 

I can go with ext4 for the format of the external drives.  I had selected NTFS a long time ago when sharing btw Linux and Windows, and forgot the reason. Also the new seagate drives came formatted NTFS and I thought they should know what was "best."  I will switch.

I do not believe I am using gvfs anywhere.  I will endeavor to avoid it.   

Months ago, I was experimenting with zfs  which  was promising for sharing between Linux and Windows, especially because I could convince it to be case insensitive with the filenames.  I do not think I would use zfs on my external usb disks.  I had tremendous difficulty removing (permanently removing) my zpool from my Ubuntu 16.04 system, and later read about bugs where other people had the pools coming back to life after reboot.  I never resolved that.  Otherwise, my experience with zfs was very positive.  Comments would be welcome if you have time. 

With the LiveCD boot, I was trying to figure out whether the RAM or CPU was compromised due to YUMI launching Ubuntu Live.  The speed felt like something from 1984.    Does YUMI cause overhead or does the Ubuntu system take over all resources when it is launched and the slow-down was purely due to the queuing issues over USB?   That matters because I have been contemplating the wisdom of having a personal computer on a usb stick, that I could use when travelling, if someone were willing to let me boot to it.  Again, comments would be very welcome. 

I will read up more on FUSE.  I had seen those letters and didn't realize they meant Famously Underwhelmingly Slow Effort.

Thanks.

---

### Post by TheFu on 2018-10-30
All consumer storage comes formatted for the most popular OS's file systems.  They are only a general "best" for those systems, not Linux.

If you let the GUI mount the drives, then you are using gvfs.   If a file manager has an EJECT icon next to the external storage, it is definitely using gvfs. If you don't know, then assume it is GVFS.

I wouldn't use ZFS on USB-connected storage, ever.

Case sensitive filenames is something that **every** OS made has, except 1.  Get used to it.

yumi isn't involved after the booting setup is created.  It is a tool that makes a boot loader work, but it isn't installed on that media.
USB is the slowdown.

There are a number of reasons why travelling with just a Flash drive for your OS isn't sufficient.  I travel a little. If you stay in any chain hotel, forgetaboutit.  Their public computers will have specialized networking required to access the internet. Your flash OS won't know anything about that. If you are staying with friends or family, perhaps it will be fine, but your setup having all the correct drivers for their network cards or wifi devices is very slim.

I've tried travelling with laptops, tablets, netbooks, and different smart-devices.  How successful you are completely depends on the correct type of networking being available wherever you stay and what you need from the device.  I need a lite-Linux distro.  After trying lots of other solutions, this is what works for me, without compromise except CPU performance.

---

### Post by starlightflyby on 2018-10-30
Again, thank you.

Let's say I was mounting an external usb (re)formatted with ext4.      If I use "sudo mount /dev/sdb1  /mnt/seagate2tb"  syntax from Terminal, does that use gvfs ?    That is what I was doing because I had no gui access because lightdm login was looped.

Case-sensitive, agree.  

YUMI ok got it.  Was worried; now shocked at how overloaded the usb channels can get.  Channels, queues, something.

What about automatic mounting?  Yesterday I used the Ubuntu 18 disks gui tool to look at the partitions, and used its Settings gear to auto mount 1 Ext4 partition of the internal hybrid drive.  Is that good/fast/optimal ? 

Agree about hotels and relatives and networking.  All true.   What hardware did you end up running the lite-Linux distro on?

---

### Post by TheFu on 2018-10-31
Typing mount from a shell does avoid GVFS, but not necessarily FUSE.

I would assume and GUI tool uses GVFS for mounting.  I've never used any disk GUI tool to mount stuff that was a permanent mount or where I needed performance.  Sometimes, I use caja to access SDHC or tablet or smartphone storage, but those all use very slow GVFS or MTP methods.
If you want "automatic mounting", there are 2 methods that I know.  fstab and autofs.  I don't have Ubuntu 18 here, but doubt any GUI would setup the fstab or autofs to do the proper mounting.  If the mount options show "gvfs" anywhere, be suspicious, even if it does modify the fstab.

For travel, I've used many different devices in my quest for what worked best for me.  I'm still looking for a better answer, but I'm cheap enough that I will use whatever until it is completely unusable first.  I'm on a Toshiba 2015 Chromebook now. Previously, had an Acer C720 chromebook.  Before that, had an Asus Eee and before that I tried to travel with a high-end Android tablet.  Before that, I had a Nokia N800 running Debian. That's over 10 yrs of devices and probably 500K airline miles.

Both chromebook devices were wiped and boot directly into my Ubuntu with Openbox setup. I don't use any DE.

For my needs, Android isn't sufficient. I have other requirements around screen resolution, weight, battery life, RAM, and good-enough performance. I don't need great CPU performance or any fancy GPU, but the GPU needs to handle playback of videos. Of course, there's a price limit too.

---

### Post by starlightflyby on 2018-11-04
I checked the Ubuntu DISKS (gui) utility and it does mention x-gvfs-show  as a default option (on a line with no prompt).  Screenshot included. 

I will look for fstab and autofs syntax to mount it.  This is for my internal 2tb hybrid disk which I do want auto-mounted.   

500k mileage: that's a lot of security hoops.[IMG]https://i.postimg.cc/65TSTCMw/Ubuntu-Disks-Screenshot-from-2018-11-05-01-11-19.png[/IMG]

---

