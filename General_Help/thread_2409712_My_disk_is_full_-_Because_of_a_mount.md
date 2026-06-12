---
title: "My disk is full - Because of a mount?"
date: 2019-01-05
forum: General Help
---

### Post by chris230291 on 2019-01-05
Hi. I have a ZFS filesystem mounted at /mnt/RAID for storage. My system disk is full and it seems it's because of that mount point.

[ATTACH=CONFIG]282105[/ATTACH]

Is this normal behaviour?

I have Transmission inside a Docker container with /mnt/RAID/Downloads passed to it. I would have thought that meant "RAID" (the zfs filesystem) was being accessed by Transmission, but it seems it has been writing to the system disk?

Any help on how to set this up is apreciated.

Chris

---

### Post by CatKiller on 2019-01-05
Why do you think your disk is full?

Baobab will always add up to 100%.

---

### Post by Impavidus on 2019-01-06
The percentages shown by disk usage analyser a.k.a. baobab are the size of the contents of that directory compared to that of its parent directory, even when that's on a different partition. As the root directory is its own parent, it's always at 100%. If you want to analyse disk space usage by command line, try these:```
df -h
sudo du -xh --max-depth=1 / | sort -hr
```The first will show disk space usage for each mounted filesystem, the second will show the size of the directories in your root filesystem only.

---

### Post by chris230291 on 2019-01-06
I know my disk is full because I got errors in the Transmission web UI. I checked in disks and it was at like 98% or something. There should be just over 100GB free space on my 120GB boot drive.

I ran [COLOR=#000000][FONT=&amp]df -h[/FONT][/COLOR] as you suggested and noticed that it only listed 3 of the 4 datasets that should be, and sure enough "Downloads" was the one missing. What would cause it to not be mounted?

Chris

EDIT: here are some commands showing that "Downloads" is not mounted... for some reason.

chris@Server:~$ zfs get mountpoint RAID
NAME  PROPERTY    VALUE       SOURCE
RAID  mountpoint  /mnt/RAID   local
chris@Server:~$ zfs get mounted RAID
NAME  PROPERTY  VALUE    SOURCE
RAID  mounted   no       -
chris@Server:~$ zfs get mounted RAID/Downloads
NAME            PROPERTY  VALUE    SOURCE
RAID/Downloads  mounted   no       -
chris@Server:~$ zfs get mounted RAID/Stuff
NAME        PROPERTY  VALUE    SOURCE
RAID/Stuff  mounted   yes      -
chris@Server:~$ zfs get mounted RAID/Software
NAME           PROPERTY  VALUE    SOURCE
RAID/Software  mounted   yes      -
chris@Server:~$ zfs get mounted RAID/Media
NAME        PROPERTY  VALUE    SOURCE
RAID/Media  mounted   yes      -

---

### Post by chris230291 on 2019-01-06
OK I exported and reimported my ZFS pool multiple times and finally its mounted correctly.

Problem solved.

Thanks for telling me that command @[Impavidus]("https://ubuntuforums.org/member.php?u=1417721"), pointed me towards the issue.

---

