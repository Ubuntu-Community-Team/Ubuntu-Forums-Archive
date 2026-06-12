---
title: "File disappeared when moved..."
date: 2012-11-19
forum: General Help
---

### Post by mikeebean on 2012-11-19
I'm running Ubuntu 12.04 with Unity, and I mounted a USB stick with 12.10 Gnome 3 installed on it.

From the desktop folder of the USB stick I dragged a text file onto the 12.04 desktop, expecting that the file would be copied. Instead it disappeared from the USB stick, and it didn't appear on the desktop. Can anyone suggest a way to find or recover this file? Thanks!

---

### Post by lisati on 2012-11-19
First of all, let's eliminate the "obvious": Did you use "safely remove device" before removing the USB stick?

---

### Post by mikeebean on 2012-11-19
I haven't yet removed the USB stick, it's still mounted, and no data has been written to it since the file disappeared.

---

### Post by stinkeye on 2012-11-19
I thought the default was copy when drag and dropping across partitions.
Maybe a bit late but nautilus will give me the option under the edit menu
to undo a move or copy action.

---

### Post by HermanAB on 2012-11-19
What sort of file system is used on the schtick?  The default is usually FAT32, though some of the bigger ones use NTFS.  In both cases, if the file was really deleted, then you should be able to undelete it with a Windoze utility, or with Photorec on Linux.

My first action would be to unmount the schtick, remove and replug it to mount it again and see what really happened.

---

### Post by mikeebean on 2012-11-20
Both file systems are ext4 according to TestDisk. Removing and remounting the stick made no difference. I wish I'd thought to Undo before I did other things, that probably would have fixed it.

I hunted for the file for a while, hoping it was in a temporary directory or something, but I finally decided to brave TestDisk, found the deleted entries on the stick and restore them. In the future I'll just copy and paste instead of drag and drop. :)

Thanks for the help! The Ubuntu community has been helpful and welcoming to me as a new user, and it's very appreciated!

Michael

---

