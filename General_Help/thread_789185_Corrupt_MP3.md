---
title: "Corrupt MP3"
date: 2008-05-10
forum: General Help
---

### Post by Funky91 on 2008-05-10
Hello,

I have a flash MP3 which seems to have become corrupt. The MP3 will not recognize any music and the drive will not mount.

Is there any hope of fixing it?

Thanks

---

### Post by ryanhaigh on 2008-05-10
You could try formatting the partition on the mp3 player. There may be a way to do this directly through the player or you can use gparted (install first then look for partition editor in system>admin BE CAREFUL!!) it would probably be easier to do in windows though (my computer>right click on player>format). You probably want to use fat32 as the filesystem.

---

### Post by sekinto on 2008-05-10
It probably uses a FAT32 filesystem, but you should check the device's manual. You can use gParted to reformat it. It may have some system files though, if so you will have to reinstall the software/firmware on it, you can probably get that from the manufacturer's page.

---

### Post by vanadium on 2008-05-10
No reformat needed, probably. Probably, you will be able to "repair" the file system using dosfsck under Linux or chkdsk under MS Windows.

---

### Post by Funky91 on 2008-05-11
Thanks for the suggestions.

What command would I use to try the dosfsck thing?

---

### Post by vanadium on 2008-05-12
What about "dosfsck"? "man dosfsck" will show you the manual.

* The device you want to check must be unmounted (no problem for you because it is not mounted in the first place)
* you should know the partition name of your device. "sudo blkid" lists them all, or you also could use "sudo fdsik -l"
* You then run dosfsck like

sudo dosfsck -a /dev/sdc1

-a does an "automatic" repair. You can also use -r for an "interactive repair. Only when using these options will you actually perform repairs. Otherwise, it is just a check, but nothing is written to the disk.

---

