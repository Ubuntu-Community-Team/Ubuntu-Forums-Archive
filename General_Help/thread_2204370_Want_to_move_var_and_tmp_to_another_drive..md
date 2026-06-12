---
title: "Want to move /var and /tmp to another drive."
date: 2014-02-08
forum: General Help
---

### Post by Bucky Ball on 2014-02-08
Hi all,

* Just bought an SSD and as the title suggests, want to move var and tmp (and the /swap file but okay with that, thanks). Now, the swap I'm pretty okay with, the other two, not so sure. I have researched quite a bit and found a few methods, but wondering if someone can give me a definitive answer that is going to work. My idea is to move these to an old IDE 7200RPM drive. 

* My second question is: is this a good idea? Do these files, tmp and var, need speed or quite happy to be accessed at a leisurely pace?

* Thirdly, should I also move /usr to the second drive? 

* I mention this fourthly in case it makes a difference; I have beefed up my old desktop with 4Gb of RAM and the SSD so it can begin the second phase of life as a Linux DAW (digital audio workstation). This will be, and from this moment forth is, its sole purpose. With this in mind, is there anything else that I should be relegating to another drive that doesn't need the speed and would be better out of the way of digital audio processing? 

FYI, the 7200 IDE I'm intending to use for this move plays NO part in the audio processing (directly, in any case, or does it?). That is all taken care of by the SSD, a SATAII 7200rpm 'recording' drive and another identical SATAII drive for soundfonts/effects/etc. The IDE will be for /var /tmp /swap, and possibly /usr. only.

Reason for IDE? I do have a SATAII drive I could use for this, but only four SATA ports on the motherboard, meaning, unless I fancy taking the side of the box off regularly, I have no eSATA speedy backup, only USB. Using IDE gives me a spare eSATA port. ;)

Using 12.04 minimal install, xfce4. Apparently this move is easier on 12.04 than previously.

---

### Post by pqwoerituytrueiwoq on 2014-02-08
i did this a couple times, i cant find the thread i made atm
i booted a live usb and used sudo cp -av to copy the stuff and edited fstab with the partition info
then i deleted the stuff i copied on the original partaoion
then i used sudo cp -av to copy the remaining files to the ssd
and updated fstab again with the new root partition id and dont forget to edit grub.cfg with the new root uuid
i used a spare hdd for holding same stuff temporarily
i put /tmp on ram /var, /home, and /root on a hdd
here is my fstab file for a example
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d842f936-1037-4cd8-96b1-b43e104b4bb0 /               ext4    noatime,discard,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=b8362e2b-2cdb-40f4-a2a8-a9ed1207cb81 /home           ext4    defaults        0       2
# /mnt/iso was on /dev/sdb5 during installation
#UUID=156f2dd4-0bfe-414c-95a8-080973d9bedc /mnt/iso        ext4    defaults        0       2
# /mnt/virtual_box was on /dev/sdb4 during installation
#UUID=03cc0da7-dc02-4f82-832a-805f8c2e6c4d /mnt/virtual_box ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=3d1dd4e3-d423-4802-b52a-aa74d6fdc8bd /var            ext4    defaults        0       2
# /var/cache/apt/archives was on /dev/sdb3 during installation
#UUID=39fbf8c6-5d6f-49b2-8433-c06f58278d36 /var/cache/apt/archives ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=edcffc51-e736-474e-b338-18182e372f87 none            swap    sw              0       0
# /tmp was moved to RAM after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777 0       0
# /root was moved to /home/root after installation
/home/root                                /root           bind    defaults,bind   0       0
# /media was moved to RAM after installation
tmpfs                                     /media          tmpfs   defaults,size=1M,mode=755 0       0
```
/tmp likes speed but it is a high write environment, it will eat away at a SSDs life, probably not as fast as /home
/var is also a high write environment due to /var/log and /var/cache
only time i ever have any lag is when i start using swap to the extreme levels. i would put swap on a 3ed disk drive but it is so rarely used i don't want to add the vibrations
if i were dual booting with a hdd for linux and windows i woudl have a paging file on the linux hdd and a swap on the windows hdd

---

### Post by Bucky Ball on 2014-02-08
Thanks for that. In other words, if I wanted to copy /var to /media/IDE_drive/var, I would use:

```
sudo cp -av /var /media/IDE_drive/var
```

? 

I understand the changing the fstab stuff. Also, I am not intending to move /home, just the directories I've mentioned - /var, /tmp and /usr if someone can give me the pros and cons of moving it - as /home won't see much action. A few PDF's and that's about it. Any directories in there will be symlinked to elsewhere and all the output from audio programs will reside in drives other than the SSD (so /home will probably only have /Documents in).

I also thought putting /home on an IDE drive might slow things down and negate the speed benefits of having the SSD in the first place as it has all user settings which probably need to reside somewhere fast. Or not?

All thoughts and suggestions welcome. ;)

---

### Post by buzzingrobot on 2014-02-08
There is a good explanation on the wiki someplace about moving a /home partition safely. It could easily be adapted for any partition.

if /tmp, /var, /usr are directories, not distinct partitions, moving them is much easier.

Unless you make constant use of swap, I'd leave it alone.

If they are partitions, be very careful editing fstab.  Typos and other mistakes in it will prevent booting.  Have a way on hand to boot from something else, mount the drive with fstab and fix it.

---

### Post by Bucky Ball on 2014-02-08
> **buzzingrobot said:**
> There is a good explanation on the wiki someplace about moving a /home partition safely. It could easily be adapted for any partition.

I was thinking it must be similar actually and will look into it. 

> **buzzingrobot said:**
> if /tmp, /var, /usr are directories, not distinct partitions, moving them is much easier.

They are directories but was intending to put them onto partitions on the other drive.

> **buzzingrobot said:**
> Unless you make constant use of swap, I'd leave it alone.

Don't actually know! Never check. 'top' tells me I am using about half of 4Gb, now I do look, and I'm thinking that can't be right. Don't have a lot going on.

> **buzzingrobot said:**
> If they are partitions, be very careful editing fstab.  Typos and other mistakes in it will prevent booting.  Have a way on hand to boot from something else, mount the drive with fstab and fix it.

I generally backup fstab before a major op like this. I also have four installs so can pilfer one if required and rejig. ;) Yep, up to the eyeballs in fully loaded USB dongles! Just bought a five pack the other day (well, five separately, actually, was cheaper!). 

Thanks for the input. Still digging and reflecting before I start wrangling with the hardware.

I'm just wondering if it's as easy as this:

1/ Boot from live media;
2/ Copy the contents of the /var directory from source to the /var partition on drive two (target);
3/ Delete source /var (drive 1);
4/ Tweak fstab to reflect the changes;
5/ Reboot;
6/ Cross fingers.

? Should I be putting them into partitions if this makes it trickier? Better to make a partition on drive 2 and copy them verbatim as directories into that? Any advantage to one or the other?

---

### Post by pqwoerituytrueiwoq on 2014-02-08
as far as your home directory there is firefox cache files for example
IIRC i did it like this 
```
cd /media/$USER
sudo cp -av oldPartition/var/* newPartition/
sudo rm -rf oldPartition/var/*
sudo nano oldPartition/etc/fstab
#update fstab for new /var partition
```
i keep /usr on my ssd myself
you don't want a var folder on the new partition as it is the var folder's content

---

### Post by oldfred on 2014-02-08
I have seen many other do like what you are doing and move some partitions to a hard drive.

You can use the move /home:
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

 Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)

      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

But two years ago I bought an relatively inexpensive SSD that was Microcenter's house brand. Not nearly as fast as new one's today.
Some have posted that new SSDs will last just as long as hard drives.

And my logic is I want every hard drive to be fully bootable without any others, but allow errors on mounting swap or data from other drives and have a fully bootable version of Linux on every hard drive.

So I have kept all system partitions on SSD, but swap which is almost never used and all data is on rotating drive.
Some also suggest mounting the temporary files in memory to both speed things up and save use on SSD. May even be a good idea with any install. But I have 4GB of RAM and did not allocated temporary files. If I had more than the 4GB I would do that also.

I do use noatime in fstab, changed from fstab trim to a cron job.

 You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.

Info on trim and ext4 without journal, ext2 does not support trim, with newer SSDs realtime a reasonable alternative to noatime and works with some apps that need timestamps like mutt


 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.

      
 Trim in 14.04 - looks like weekly?
[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)

I made my script daily.

        Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim


```
 #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

 

```

---

### Post by Bucky Ball on 2014-02-09
Firstly, thanks everyone for the input.

I have trimmed with a daily cron job (I'd been looking at that page and did it just before you posted oldfred), but I'm not finding any log in /var/log/trim.log. So no idea whether that's working but perhaps I have something wrong:

```
#!/bin/sh
LOG=/var/log/trim.log
echo "* $(date -R) *" >> $LOG
fstrim -v / >> $LOG
```

/swap and the Firefox cache are both on the IDE drive and things are rolling along nicely. Seems to be no degradation in performance of either the machine or Firefox. I had a look at conky and the only thing that's shocking the system is Shockwave; sending the CPU to a constant 50%. I've now changed that to asks me before it butts in and all is purring. RAM barely moving and /swap empty. 

I have decided that, rather than move /var entirely, it might be better to move the parts that I can live without if one of the drives crashes (and this is following oldfred's thoughts about wanting the install on the one partition; I can see the point in that so I'm only intending to banish things I don't mind losing in case of disaster).

So have been trying to get my head around moving just /var/log and possibly /var/cache to the other drive along with /tmp. Not sure how they'll go on such an old drive, but right now I have the time, and the inclination, to find out. I am still not confident with any method I've found, though. 

My plan was this, and perhaps people can let me know if it's feasible. 

1/ Boot from the SystemRescue USB and copy the contents of /var/log to /media/var/log1;
2/ Rename, rather than delete, the original /var/log;
3/ Rename /media/var/log1 to /media/var/log;
4/ Tweak fstab to mount /media/var/log at boot.

Repeat the dose for /tmp and /var/cache if I go there. 

At this point, my remaining questions are:

A/ How do I write the lines for the fstab? Fine with adding a partition, but never added a single directory before, and;
B/ Is my plan for /var/log, /tmp, and possibly /var/cache going to work as outlined above?

Thanks again for the input. ;)

(PS: Just to reiterate, I'm not moving /home. They'll only be the settings in it, they'll be hidden, and there will be maybe one symlink in there linking to a /Documents folder on the IDE. This is a multimedia box so all multimedia will be stored on different drives and accessed from the drive directly. Cheers.)

(PPS: @oldfred, the second link in your post was dead for me. The rest were, as usual, informative.)

---

### Post by Bucky Ball on 2014-02-10
Still not getting a trim.log so not sure that's working. Have been doing it manually once a day since I created the cron.daily job. Will post another thread regarding that if problem persists, which I think it shall. :-k

Still hunting down specifics re. moving /var/log before I'm confident to do it. I think I'm across the moving of it, but still unsure about the fstab line and exactly what it should contain ... apart from '/var' somewhere, probably twice. If it were a partition I'd know to just stick the UUID in there. But for this?

Guess I could create teeny partitions for /var/log and /tmp, but don't really want to do that. Would rather keep them in a directory on the other drive. Hmm.

---

