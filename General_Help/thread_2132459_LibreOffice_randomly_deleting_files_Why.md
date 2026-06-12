---
title: "LibreOffice randomly deleting files: Why ?"
date: 2013-04-04
forum: General Help
---

### Post by GameX2 on 2013-04-04
Hi,


I have a really annoying issue.  I have a friend who's doing a work experience in an elementary school (Kids from 6 to 12 years old),  The school is using Ubuntu 11.04;
Sure, installing Ubuntu 12.04 would avoid having to upgrade frequently; I don't know what you guys think, but on another point of view, I guess they do basic stuff like web browsing or text formating with LibreOffice.  There is also a very high possibility (Just guessing) that the school is "afraid" of Unity.  This is also understandable, since Unity require most typing and is maybe less user-friendly for kids than GNOME2.  Maybe they do not want (Or do not know how) to install Gnome-Session-Fallback.

Well, back to the problem: my friend (who's not a Linux user) just told me if I was able to recover lost ODT files.  For a really weird reason, LibreOffice seem to erase the files, once the user copy the .ODT to a USB drive (FAT32, I suppose).

I did a few ressearch, and it was my first attempt ever of file restoration on Linux.  I installed Foremost, typed the command to scan for ZIP files (As recommended) on the USB drive, and surprisingly, the program was able to find all the 3 ODT files that were lost! :O

Waow, that's impressive.  That was my first attempt ever, and I managed to restore documents lost by kids! :D  So proud! :D

Anyways, I'm asking if someone know why LibreOffice Writer "erase" some ODF files when (probably after) they get copied on the USB drive.  I've checked, and the files were not hidden.
This is not an isolated case - the problem has occured to one teacher, and a few students as well.  I'll have to try and restore the files from these persons as well.  That's definitely weird.

What if the file system was EXT2 (Honnestly, I have no clue about it.  I never went into that school), which is less stable than EXT3 and EXT4 ?

Set LibreOffice Writer to auto-backup in the Settings is not an option, since the school is using a "Guest" account, so the files get wiped, after logoff.

Could using Ubuntu 11.04, which is End-Of-Life, be the cause of this?  I can understand the school currently use 11.04, for simplicify reasons, however.  Maybe that the hardware is old, and I know by experience that Ubuntu 12.04 run slow on a 1.5 GB of RAM Pentium 4 (Even with Gnome-Session-Fallback).

Or maybe unsafely unplug a USB drive from Linux is the cause of that (Simply that) ?  Does this happen often ?

If anyone got ideas about why this happen, please let me know!

---

### Post by Impavidus on 2013-04-05
Unsavely unplugging the usb drives may be the cause, but I'm not sure. By default I/O to these drives happens asynchronously, which is better for drives in general and flash drives in particular, and is also faster. These drives are automounted, but I think it must be possible to set the **sync** option on them. I don't know how. If this is done, it will be saver to just unplug the drive.

If there is fear for Unity, I suggest trying Xubuntu. It has long term support, has an installation disk that requires no tweaking after install and has a familiar user interface, with nice point-and-click menus. Although I don't really think the kids will care for UI familiarity. Libreoffice doesn't come preinstalled, but can be installed in a few clicks.

---

### Post by GameX2 on 2013-04-05
> **Impavidus said:**
> Unsavely unplugging the usb drives may be the cause, but I'm not sure. By default I/O to these drives happens asynchronously, which is better for drives in general and flash drives in particular, and is also faster. These drives are automounted, but I think it must be possible to set the **sync** option on them. I don't know how. If this is done, it will be saver to just unplug the drive.

If there is fear for Unity, I suggest trying Xubuntu. It has long term support, has an installation disk that requires no tweaking after install and has a familiar user interface, with nice point-and-click menus. Although I don't really think the kids will care for UI familiarity. Libreoffice doesn't come preinstalled, but can be installed in a few clicks.

Thanks.  I also thought about Xubuntu, I know it run pretty smooth on an older Pentium 4.  The school prefer prefer to stick with Ubuntu, since they've used it since a while, I don't know.  I do believe Unity is a bad choice in that case.  Perhaps that typing the name of the application in the Dash isn't the greatest thing for kids.

---

### Post by Vaphell on 2013-04-05
yes, unsafe unplugging is most likely the culprit. OS abstracts disk operations away but what really happens under the hood is OS, device and filesystem specific, there is no guarantee it will work fine everytime. Data simply might not get committed yet if the usb drive is removed right after copy or whatever. 'Safely remove' simply forces commit
Note that there were (still are? not seen complaints in quite some time) issues with Open/LibreOffice and ext4. Ext4 was finetuned for greater transfer speeds but that comes with more buffering and more potential delay. In case of power loss or things like that some people were getting their doc zeroed (iirc caught in the middle of creating new version of the file before filling it with content).
Working on single existing copies of documents is a very bad idea - backups and versioning (saving from time to time with a different name) are the way to go, so you have always something to fall back on.

---

### Post by GameX2 on 2013-04-06
Thanks the replies.

Despite all my efforts, I've never managed to recover the lost ODT files from the teacher (XD).  I've tried several (6 or 7) Windows programs, and a few well known Linux tools as well (Foremost, Photorec along with Testdisk, Scalpel..).  They keep finding the same files, not these I'm looking for.

I've noticed the USB drive was formatted in FAT16 (Waow, that's really old.  Was used by DOS / Windows 95 before OSR2 !).  I assume this file system is not really stable.
Should I format the drive in FAT32 after backing up the files on it (I'm aware I wouldn't be able to restore the files after that.  Really tried my best) ?

---

### Post by Impavidus on 2013-04-06
I still have a 1GB FAT16 usb stick (7 years old), and it's still my main one. OK, I once lost a part of a large PostScript file (no problem, there never are any files on the stick that aren't anywhere else too, and I could regenerate the file from the source), but I found that as long as I keep that large file on the stick no other files are damaged. You can format it to something else, but I don't think FAT16 is unreliable. It's just not fit for big drives and misses some modern redundancy (IIRC).

---

### Post by GameX2 on 2013-04-06
> **Impavidus said:**
> I still have a 1GB FAT16 usb stick (7 years old), and it's still my main one. OK, I once lost a part of a large PostScript file (no problem, there never are any files on the stick that aren't anywhere else too, and I could regenerate the file from the source), but I found that as long as I keep that large file on the stick no other files are damaged. You can format it to something else, but I don't think FAT16 is unreliable. It's just not fit for big drives and misses some modern redundancy (IIRC).

It's a 1GB stick.
Am I wrong saying that if the file system was in FAT32, I would have more chances to restore these lost files?
Maybe not?

---

