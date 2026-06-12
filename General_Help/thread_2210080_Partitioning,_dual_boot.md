---
title: "Partitioning, dual boot"
date: 2014-03-08
forum: General Help
---

### Post by ghost25 on 2014-03-08
Okay, so I decided it was time to start cleaning out a laptop that dual-boots Win7 and Ubuntu 12. I figured I should do this because my brother gave it to me, and said it had stopped working. What he did to it, I don't know. What I do know is that according to Disk Utility my Ubuntu partition has only 105MB, and the Win7 partition has 160; this is all on a 320GB drive. It looks like I have five partitions (?!) on here, only three of which are actually being used. What a waste of space!

I've installed and played a bit with GParted, but it warned me off of doing what I wanted to do, namely, shrinking and moving my Win7 drive to allow more usage by Ubuntu for updates. 


[ATTACH=CONFIG]250980[/ATTACH]


This is what my Disk Utility tells me is going on, and why I'm getting confused. I basically want to eliminate one of the partitions that's free, and have 4 in total; one for each OS, and one for the files saved within each OS. I figure out of a 360GB drive, 90 would be more than enough for Windows to have the OS in, and I don't store that much in Windows. I figure to allow maybe an extra 10GB in the Ubuntu partition after I do updates, to allow for future changes, then have evenly divided the last two partitions for file storage. Is this something that I can even do? If so, how would I go about doing it so that Win7 and Ubuntu both work? And, finally, would I actually need to have 4 partitions, or would it work to have 3, since Win7 and Ubuntu can pretty much access the same user file types?

This might be stupid, but thanks for any help you guys can offer.

---

### Post by Bashing-om on 2014-03-08
ghost25; Hello,

My oh my, That does not look good for the home team.
1 - a small boot partition
2- 160 GB NTFS (windows) partition
3- 3.2 GB free, so does not count as a 'partition' -> free space unassigned
4- 78 GB swap (REEKS BIG TIME) as an NTFS partition, should be file type 'swap' and say 2 GB !!
5- 78 GB free, so does not count as a 'partition' -> free space unassigned .

Nowhere is there a partition for the ubuntu install !

So, let's get a better look at the hard drive.
Post back a screen shot of what "GParted" shows;
AND
post back the output - between code tags -of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And get prepared to install ubuntu from scratch.

[INDENT][INDENT]what will be
[INDENT][INDENT]will be
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ghost25 on 2014-03-08
Thanks for the reply, Bashing-om. First things first, the terminal outputs:

sudo disk -lu returns ```
sudo: disk: command not found
```
sudo parted -l returns:
```
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type     File system  Flags
 1      1049kB  106MB  105MB   primary  ntfs         boot
 2      106MB   160GB  160GB   primary  ntfs
 3      163GB   242GB  78.4GB  primary  ntfs
```

and sudo parted /dev/sda unit s print gives:

```
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start       End         Size        Type     File system  Flags
 1      2048s       206847s     204800s     primary  ntfs         boot
 2      206848s     312682495s  312475648s  primary  ntfs
 3      318973952s  472066047s  153092096s  primary  ntfs
```

And here's the screenshot as you requested.
[ATTACH=CONFIG]250988[/ATTACH]

EDIT: I also switched briefly into SU mode to see if it was a command incapable of being performed by the average user, and nope, the command #disk -l# simply isn't a valid command on my system.

---

### Post by Topsiho on 2014-03-09
I think Bashing-om made a typo and meant fdisk -lu in stead of disk -lu.

I agree with them ( :) ) that the partitioning as is shown in GParted is a little strange, and wonder whether Windows runs correctly on this computer. Usually, as far as I know, Windows wants to run in the first partition, which is sda1, it appears that on your computer Windows is installed in sda2.

I think Ubuntu has lots of space to run in the large unallocated area. As already 3 primary partitions are in use, Ubuntu must be installed in two or more LOGICAL partititons within this area. Which is fine for Ubuntu.

But let Bashing-om do the talking :)

Topsiho

---

### Post by Mark Phelps on 2014-03-09
The first partition on the drive is the Windows boot partition; the second is the OS partition.  This is a "normal" installation for when Windows 7 is installed to a blank hard drive.

The presence of the /host mount point indicates that this is a Wubi installation -- in which Ubuntu exists inside a single file (root.disk) on one of the Windows NTFS partitions.

---

### Post by Topsiho on 2014-03-09
Ha, Mark Phelps, thanks for this information :)

Topsiho

---

### Post by Mark Phelps on 2014-03-09
To the OP: Your distro is installed INSIDE a Windows  NTFS partition -- which is why GParted won't show it anywhere.  IF you shrink the partition containing it using Gparted, that is almost certainly going to corrupt it and render it unusable.

To find out which partition, look in the Windows filesystem for the file root.disk.

Wubi installations are limited in size, so you can't expand it beyond the 30GB limit, period.

Wubi is also a bad idea these days as it has been dropped -- due largely to complications in getting it working with the recent new Win8 PCs.

---

### Post by ghost25 on 2014-03-09
Hey all, thanks for the replies. While this more or less makes sense and sounds good, I bet y'all are wondering why the drive is this balled up in the first place.

I acquired it from my brother who is a self-professed geek, but doesn't know half of what he's talking about. He had this laptop before me, and ended up giving it to me and buying a new Win8 PC due to an unknown problem. I figured the problem out in about 30 seconds, which was a loose stick of RAM. The only thing he told me to do was to wipe his data and I could have it. 

He also told me that Ubuntu had stopped working (it hadn't, but with how screwed up this system is, I can see why the Ubuntu OS took forever to load. I got fed up with waiting for fifteen minutes myself and rebooted it, which got boot time to about 14 minutes.

I intend to keep Win7 loaded on this just so I can sync my phone, I'm also doing online job applications that unfortunately require Windows to do correctly so I need to keep it a dual-boot. I believe I have everything from both OSes backed up, as I just bought a huge external hard drive for just this purpose. I really don't want to erase and completely redo Windows though, because I don't have the recovery disk and y'all know how Windows is about someone else using the OS.

That also sounds right for Windows being installed on the first two partitions, because this device obviously had Win7 on it when it was bought from the store, and I've yet to see a retailer sell a non-OS laptop.

As far as the output for sudo fdisk -lu, this is it:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde1c2d32
```


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   312682495   156237824    7  HPFS/NTFS/exFAT
/dev/sda3       318973952   472066047    76546048    7  HPFS/NTFS/exFAT

---

### Post by oldfred on 2014-03-09
Several suggestions related to keeping Windows and installing Ubuntu dual boot.
Depending on how much you may use Windows vs. Ubuntu.
If no data in sda3 delete it. Or backup first.
Create a 20 or 25GB / (root) partition formatted ext4.
Make the rest of the drive an extended partition. swap & data or /home will then be logical partitions inside extended.
Inside extended at end put 2GB for swap, assuming you do not hibernate.
Use remaining space for either /home or a NTFS data partition for shared data between Windows & Ubuntu.

Always best to backup Windows and make a Windows repairCD/flash drive before any major install. Error happen and having backups allows recovery.

---

### Post by ghost25 on 2014-03-31
Hey all, sorry for the delay in response. Holy crap though, I'm starting to look at all this sh*t, and I'm wondering if I wouldn't be better off just starting from scratch?! This entire thing just seems worse and worse the more I look at it. And, TBH, I'm not sure if this is actually going to be worth the hassle? I've had to completely redo systems in the past, so it's not like I'm against the idea, I guess I just wanted to see if I could clean it up without having it completely screw everything up. 

If I were to decide to just throw in the towel and redo everything from the base up, would it make more sense to install Ubuntu first, or Windows (from the backup/restore flash drive I made)? I get that Wubi turned this into a massive pain in the ass, which is making me wonder just how badly my brother screwed up this install to begin with!

Thanks for continuing to help me out.

---

### Post by Bashing-om on 2014-04-01
ghost25; Hey,

Your system, it is up to you what you want to do. However, I my humblest Of Opinions, in the long run you will have greater confidence in your operating system if you (RE-)install and start over from scratch.
To that end, my suggestions:
Install Windows 1st;
defrag windows, some say 2 times;
in windows set up "unallocated" space for ubuntu -> so you can do a true dual boot;
In Windows, run the check disk utility;
Reboot a couple of times, -> makes sure all is good,

install ubuntu, using the install option "something else" -> and install into the "unallocated" space.

As WUBI no longer has support, you are better served to make a true dual boot system. If there is data on the WUBI file system you wish to keep, There are means to migrate that WUBI install onto the hard drive, with prior prudent planning.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by ghost25 on 2014-04-01
> **Bashing-om said:**
> ghost25; Hey,

Your system, it is up to you what you want to do. However, I my humblest Of Opinions, in the long run you will have greater confidence in your operating system if you (RE-)install and start over from scratch.
To that end, my suggestions:
Install Windows 1st;
defrag windows, some say 2 times;
in windows set up "unallocated" space for ubuntu -> so you can do a true dual boot;
In Windows, run the check disk utility;
Reboot a couple of times, -> makes sure all is good,

install ubuntu, using the install option "something else" -> and install into the "unallocated" space.

As WUBI no longer has support, you are better served to make a true dual boot system. If there is data on the WUBI file system you wish to keep, There are means to migrate that WUBI install onto the hard drive, with prior prudent planning.
[INDENT][INDENT]just my thought
[/INDENT]
[/INDENT]


Thanks for the reply, Bashing-om. As you say, it is my system, and up to me. However, I guess in some ways I'm a glutton for punishment lol.

Doing a bit of research myself for what WUBI is, since I'd never heard of it before now, it turns out my brother decided to use a windows installer rather than do it properly. Whoever decided to create WUBI was obviously a malicious little bastard, now weren't they? Lol.

I'm thinking that, since I do have everything from both "systems" backed up, I might just be better served by as you suggested, re-installing windows, et cetera. Nothing on my Ubuntu drive that isn't backed up is something that can't be replaced or replicated; one of the nicer things about Ubuntu IMO.

I'll let y'all know when I get this figured out and taken care of, and hopefully it won't lead to any complications. Thanks again guys.

---

### Post by ghost25 on 2014-04-02
Okay, so update time. I got Windows restored to a bare slate, if you will, but I notice that there's still 3 partitions: C (local disk, 148GB), D (Swap, 72.9GB), and F (local disk, 99.9MB). D still has the Ubuntu folder in it, which contains a link to uninstall Ubuntu (which I want to do, only so I can reformat the drive and fix the epic fail there) but it doesn't seem to work. I've run it both ways (normal and admin) with no luck, even the Uninstall-Ubuntu external downloader doesn't work, and there's nothing in my Programs to uninstall. (Brand-new install of Windows, so it has no crap on it yet, nor have I restored from my external backup)

When I reboot, GRUB still gives me the option to boot into Ubuntu, which I haven't yet done, but that tells me something is seriously wonky with Wubi. Why else would there be nothing, anywhere, to actually uninstall Ubuntu and then delete/reformat that partition? This is turning into a real head-scratcher... Thanks for any help.

---

### Post by Mark Phelps on 2014-04-02
> Whoever decided to create WUBI was obviously a malicious little bastard, now weren't they? Lol.Actually -- NO, they weren't.  They spent a LOT of time coming up with a way to allow folks to install Ubuntu WITHOUT having to deal with the risk of repartitioning -- which, if you do it wrong, is a surefire way to completely trash your PC.

The problem with using Wubi now is that it has been abandoned -- largely due to complications with the new spate of Windows8-preintalled PCs.  Using it now is a lot more complicated than it was in the past, and in general, we advise against using it anymore.

You need to remove the Ubuntu folder from your Windows filesystem BEFORE you attempt to reinstall Ubuntu. It's probably not going to affect the reinstall, but why take the chance when you don't really need it? 

If you REALLY got Windows restored to a "bare slate" (as you claim), there should NOT be an entry for Ubuntu on the boot.  But, to be safe, I would recommend the following:
1) Use the Backup option to create and burn a Win7 Repair CD
2) Boot from that CD and run Startup Repair three times -- that's right, three times.
3) Remove the CD and reboot.

At this point, you should be booting directly into Win7, with no menu and no Ubuntu choice presented.

I notice that you do not list an "E:" drive -- did you remove it? Have you confirmed, using Win7 Disk Management, that you only have three partitions on the drive?

---

