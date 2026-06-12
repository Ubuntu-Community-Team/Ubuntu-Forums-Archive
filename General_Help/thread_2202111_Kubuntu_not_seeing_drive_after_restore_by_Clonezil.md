---
title: "Kubuntu not seeing drive after restore by Clonezilla"
date: 2014-01-27
forum: General Help
---

### Post by dwlamb on 2014-01-27
Good day,

This weekend I had to restore my system from a Clonezilla backup.  The system was moved from one drive to another but the drive the o/s is loaded on remains the same, sda1.  On this computer I have a removable drive bay and Kubuntu does not see the disk.  Currently, I have a 1 Tb drive physically loaded in the drive.  The disk is not on the fstab.  Normally when booting the machine, Kubuntu treats it like any USB storage device.  It shows up on Dolphin but it is necessary to click on it to mount before it will list contents and can be used.  Nor does the drive show in /media/, where it normally mounts to.

The BIOS sees it and any of the utilities (e.g. GParted, Clonezilla, file managers) of PartedMagic see the drive.

Any USB devices I connect to the computer, including hard drives that are USB connection do appear as they should and function.

Is there something that may not have set-up properly from the restoration?  I left the rebuilding of the Grub to Clonezila.

---

### Post by Bashing-om on 2014-01-27
dwlamb; Hi ! And a great day to you also !

Hey, maybe the system thinks the drive is "locked" ?
What results from terminal code:
```

sudo lsof /var/lib/dpkg/lock
sudo lsof /var/cache/apt/archives/lock

```

Else, perhaps the system thinks the drive is in a "busy" state ?
```

sudo fdisk -lu ##to indentify the drive
fuser -m /dev/sdXY ##where 'XY" is as related by "fdisk"
/dev/sdc1: 538 ##example output
ps auxw|grep 538 ##substitute your PID here
kill -9 538 ##again with your PID
umount /dev/sdXY

```

Hey, It is a thought, else ->
[INDENT][INDENT][INDENT][INDENT]we will know more
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dwlamb on 2014-01-28
Good day,

Be darned if I know how but the mount points in /media were changed to root instead of my log-in username.  No wonder they would not load.

All is well now.  Thanks for the help.

---

### Post by Bashing-om on 2014-01-28
dwlamb; Good deal,

Strange things do happen, glad ya fingered it out.
As all is good now, please mark this thread as solved. This aides others seeking a similar solution and as well, helps keep the forum tidy.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

