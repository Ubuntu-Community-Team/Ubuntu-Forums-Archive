---
title: "ntfs drive lockup"
date: 2008-05-05
forum: General Help
---

### Post by thomascj on 2008-05-05
background:

recently installed hardy on my desktop (been using ubuntu on laptop for over a year).

issue:

every time i use the file browser to access files on a particular partition (i can almost narrow it down to a particular "area") -- the computer locks, requiring a hard reset.  sometimes it kernel panics (LED's on keyboard blink) -- also requiring a hard reset.

the disk in question is an NTFS partition containing some video files.  if i open files on the same drive from within a video player, as opposed to nautilus, they all seem to play just fine.  also, i can mount this drive, and the computer runs just fine for days at a time -- until i open nautilus and try browsing the drive.

i've used an XP disk to run chkdsk /R on the drive, which did say there were some errors, however i find it really wierd that I'm able to access the files just fine as long as i don't do it with nautilus.

any idea's?

---

### Post by Fixman on 2008-05-05
> **thomascj said:**
> background:

recently installed hardy on my desktop (been using ubuntu on laptop for over a year).

issue:

every time i use the file browser to access files on a particular partition (i can almost narrow it down to a particular "area") -- the computer locks, requiring a hard reset.  sometimes it kernel panics (LED's on keyboard blink) -- also requiring a hard reset.

the disk in question is an NTFS partition containing some video files.  if i open files on the same drive from within a video player, as opposed to nautilus, they all seem to play just fine.  also, i can mount this drive, and the computer runs just fine for days at a time -- until i open nautilus and try browsing the drive.

i've used an XP disk to run chkdsk /R on the drive, which did say there were some errors, however i find it really wierd that I'm able to access the files just fine as long as i don't do it with nautilus.

any idea's?

Try editing your /etc/fstab file, and adding a line saying
```
 (your ntfs drive) /media/ntfs auto auto,rw,user,exec 0 0 
```

Being (your ntfs drive) the device to your ntfs drive (like /dev/sda1)

Then, open a terminal and write

```
 
sudo mkdir /media/ntfs
sudo chown (your user) /media/ntfs
mount (your ntfs drive)

```

---

### Post by thomascj on 2008-05-05
no go -- rather than a hard lock or a kernel panic it just rebooted the machine.

i've tried other things as well -- such as just mounting it with a standard 

```

sudo mount -t ntfs-3g /dev/drive /media/dir

```

all other drives are mounting via /etc/fstab the same way, and allow access just fine -- that i've noticed. 

here's the fstab line they're all using:

```

/dev/sdb4 /media/data ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

---

### Post by Fixman on 2008-05-05
Can you boot from those drives? Maybe theres the problem.

---

### Post by thomascj on 2008-05-05
no idea if i can boot from them -- they're just storage drives.  never had the need to.

---

### Post by thomascj on 2008-05-06
bump

---

### Post by thomascj on 2008-05-06
> **thomascj said:**
> bump

surely someone else has had this issue before..

---

### Post by thomascj on 2008-05-08
alright.. an update:

formatted primary partition.  split it in two, installed windows XP on one, and ubuntu on the other. 

ran a disk defrag on the faulty drive in question, twice, resulting in a near perfect disk, and showing no errors.

both OS's are fresh installs, everything works fine in windows.  reboot to ubuntu, browse drive -- entire PC hard locks and reboots within seconds of beginning to browse this one particular drive.

i really can't figure out what's any different about this one (as opposed to the other 3-4 partitions/drives i have set up).  i still feel like it's got something to do with the caching of thumbnail images for an entire drive full of video files -- but what do i know.

---

### Post by thomascj on 2008-05-10
bummer -- seriously.. i've found solutions to every single little problem i've ever had with ubuntu on these forums... it's so hard to believe no one has had this problem before.

---

### Post by vanadium on 2008-05-10
[quote=thomascj]i've used an XP disk to run chkdsk /R on the drive, which did say there were some errors[/quote]

First make sure (using Windows) that the volume does not give any errors before attempting to use an ntfs volume with Linux. Alternatively, convert the volume to fat32 or better yet, a native linux file system such as ext3.

---

