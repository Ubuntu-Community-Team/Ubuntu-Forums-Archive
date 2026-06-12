---
title: "Some HW Problems"
date: 2004-11-18
forum: General Help
---

### Post by r0nin on 2004-11-18
Hello there,

I'm new to Linux, Ubuntu has been my first Distro I've installed along WindowsXP. So far I've liked it and have managed to do whatever I had done on WinXP before.

I thought HD+CDRom/ DVD-Drives should apear in the MNT dir, should they not? I've got several other Partitions (3 Windows + one other one, a whole HD), but I can't see any. Knoppix sees all of them, Windows manages to find all, except the Linux ones. I've checked the Device Manager under Linux and he sees the Partitions/ HDs there, I just cannot access them. 
Under /dev I can see the names of the partitions sda, 1... and sdb1. The files type is: x-special/ device-block.

Is there a way to force open CD drives? Under Linux I sometimes cannot open the bay to change the disk! (By either pressing the eject button/ ejecting them from Linux)

Are there programmes for Linux that alow me to see the temperatures of my CPU/ MB and change the fan-speed?

Thanks, any help is greatly appreciated  :grin:

---

### Post by dataw0lf on 2004-11-18
CD/ DVD drives should appear in the /media directory under Ubuntu.  To eject something, use the eject command.  As far as windows partitions, you will have to manually mount them:
```
mount -t ntfs /dev/hd<partition> /mnt/windows
``` 
Obviously, you will have to create the /mnt/windows directory.
dataw0lf

---

### Post by FLeiXiuS on 2004-11-18
** Thread moved to general support **

For the mount problem, in linux you have to mount a drive to view it, then unmount a drive to eject it.

To unmount you may open a terminal by right clicking on the desktop and clicking Open Terminal.

Then,  enter in the following.
```
sudo umount /media/cdrom
```

This should unmount it from the linux file system and sometimes, eject.  Mine didn't eject so I had to push the eject button on the drive.


For CPU temperatures, i would advise you to take a nice look at gDesklets.
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

Help / HOW TO's
[http://ubuntuforums.org/showthread.php?t=3012](http://ubuntuforums.org/showthread.php?t=3012)

---

### Post by wallijonn on 2004-11-18
[QUOTE=r0nin]Is there a way to force open CD drives? Under Linux I sometimes cannot open the bay to change the disk! (By either pressing the eject button/ ejecting them from Linux)[/QUOTE]

I usually will just right click the drive, eject. (You can "Add to Panel", disk). Linux will not allow you to eject a mounted drive. I also added the "Force" applet to the panel to drag it over a hung app. to force it to quit.

---

