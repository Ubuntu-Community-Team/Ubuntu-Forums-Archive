---
title: "135 Gigs of files missing"
date: 2018-08-18
forum: General Help
---

### Post by JP_Rockagetty_III on 2018-08-18
Hello,

I have an older system (please don't tell me to "just upgrade").  It is an i3-3245, Intel board, running Mythbuntu 12.04.  My Seagate 3 TB SATA drive is the only drive in the system.  It works well with my HD HomeRun Dual.  I can record, and watch live over-the-air TV as well (I am 7 km from most of the TV towers in my city, and the antennae are up on a hill, I can see them from my back yard).

I have two problems:

(1) I forgot the administrator password.  I can "break into" the system before Grub takes control, but Myth front end is set to auto-start, so I don't see the Grub screen.  How to fix this?

(2) If I need to reinstall or upgrade, I want to save the 135 Gigs of files in /home/mike/Downloads.  Mostly it is L. Ron Hubbard Scientology cr@p, audio recordings and text files.  For me, the best way to back up the files involves taking the drive out and putting it in my main machine (Asrock board, AMD 8150 chip, Win7 / Mageia 6 dual-boot, 480 Gig Samsung Evo 850 SSD).  On my i3-3245 machine, the files are in /home/mike/Downloads.  But when I put the drive in my main machine, I log in to Mageia and mount the partitions from the Mythbuntu drive, and the files simply aren't there:

```
mount /dev/sdb1 /media/sdb1
mount /dev/sdb6 /media/sdb6

cd /media/sdb6/mike/Downloads
```

(For the Mythbuntu machine, /home is on partition 6, everything else is on partition 1.)

(Don't worry, I'm not pirating anything.  During the Larry Wollersheim case, there was a bankruptcy filing, and nobody showed up to bid on those old Scientology papers and recordings, so they were declared public domain.  I want them for scholarly and/or research purposes.  And to laugh at the tortured syntax and specialized/redefined words often found in cults.)

I would love to know what I am doing wrong here.  Is there some new filesystem convention like symlinks or autofs or systemd that doesn't work properly when the drive is mounted in some other *nix system?  I have run Linux since July 1998 (Caldera OpenLinux --> Mandrake --> Mandriva --> Ubuntu --> Mageia), and I simply don't know what might be going on.

Can anybody tell me where the files went?  I used Midnight Commander  under Mageia and cannot find the files ANYWHERE on the 3TB Mythbuntu  drive.  Nothing is encrypted here.  Thanks in advance for your help!

---

### Post by TheFu on 2018-08-18
It is against forum rules to help with unsupported releases.  Support for 12.04 ended in 2017.

1) boot from a flash drive. Use a 12.04 ISO.
2) Might you be using LVM?  Check that.  But I would just use rsync to move the files over. Unplugging storage to move files is so, so, 1990 sneakernet.

---

### Post by oldfred on 2018-08-18
If UEFI system, which it should be, you press escape after UEFI/BIOS screen, but before grub. You may have to press several times or try more than once. If BIOS, you press & hold shift key from UEFI/BIOS screen until grub menu appears. 
But if UEFI and you have UEFI fast boot on, you may not have time to press any key. Then use cold boot not warm reboot, to get full UEFI start up which scans system for hardware. Fast boot assumes not changes and does no scan and jumps immediately to booting.

You should be able to use any current ISO or your working install.

Then post this after mounting, you did create the mount points first?
ls -l /media
ls -l /media/sdb1
ls -l /media/sdb6
ls -l /media/sdb1/home

---

### Post by JP_Rockagetty_III on 2018-08-19
> It is against forum rules to help with unsupported releases.  Support for 12.04 ended in 2017.

If I can't figure out what is wrong with my computer, many times I will never, ever figure it out (40 years ago I had not heard the term Asperger's Syndrome, but it explains many problems from the Commodore Vic20 right up to the present).  I have to get help from somewhere; this seemed like a welcoming place, and the best, obvious place to ask.  And 135 GB of missing files is an issue with any version of any OS.  The internet voluntarily gives support so I can figure out my old 1981 Honda, so why wouldn't it give support for old software?  Support is voluntary, after all.

(I'd rather ride my Honda 400 than a Heavy-Davidson -- I've driven both; you'll just have to trust me.)

(And why should I risk breaking the Myth TV database and losing all of my recordings?)

I did figure it out, thankfully.  The main machine (AMD 8150) had two hard drives.  So the 3 TB spinner from the i3-3245 machine (Intel DH77EB motherboard) was actually sdc.  When I mounted /dev/sdc2 to /mnt/sdc2, the files were right there.  Files copied (135 Gigs, plus I found 90 GB more), problem solved.

It is interesting to note what I found in the GPT partition table:

```
Device          Start        End    Sectors  Size Type
/dev/sdc1        2048       4095       2048    1M BIOS boot
/dev/sdc2        4096 5856550911 5856546816  2.7T Microsoft basic data
/dev/sdc3  5856550912 5860532223    3981312  1.9G Linux swap
```

Why didn't the Mythbuntu installer mark the partition as "ext4"?  The mount command (with no arguments) does reveal it to be ext4, as we always presumed it would be.

> ...so, so, 1990 sneakernet.

I'm sorry, I just don't have the networking knowledge to make the computers see each other.  It's okay though.  The last time I unplugged and moved a hard drive to copy ~300 Gigs of files, I used a modular SATA power cable from a different PSU manufacturer and burned a chip on the drive controller.  A ~100% recovery from KrollOntrack in Minnesota, USA cost me $1,400.  This time I copied the files with no damage and no expense.

Now I'll have to work on breaking in to the machine for the password reset.  And dozens of other tasks around the house.

Thanks!

---

### Post by oldfred on 2018-08-19
Glad you found your data.

fdisk, parted & gdisk all show slightly different bits of data about each partition by default. You can use parameters to show other data.


We do not support tying to get 12.04 or other versions past their life as that is both very difficult as repositories are closed and there just is no reason to be using very old versions. It can be dangerous for all of use as old systems are not patched for newer virus or any other Internet type issues.

---

