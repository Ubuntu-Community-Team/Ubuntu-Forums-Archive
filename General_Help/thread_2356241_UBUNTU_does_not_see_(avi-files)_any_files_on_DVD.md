---
title: "UBUNTU does not see (avi-files) any files on DVD"
date: 2017-03-21
forum: General Help
---

### Post by xenon3 on 2017-03-21
What must I do? Is there an additional driver I need for the File Explorer? DVD drive does play DVD movies with VLC player though. Simply does not see files burned on a DVD.

Files on a CD he can read and see.

On a DVD+RW he cannot see the (avi) files, something is burned on the DVD, one can see the burned track, is burned DVD perhaps not finalized?

DVD is burned under Windows 10.

---

### Post by TheFu on 2017-03-21
Which file system was used to burn?  Some of the Windows file systems need special support under Unix systems to be read and if the file system wasn't closed correctly during the end of the burn, nothing can help.


ISO9660 is what you want for the greatest cross-platform support.  If you need long file names, there is joilet and/or rock ridge extensions.  It has been a VERY long time since I burned any optical media on Windows, so don't quote me on those things. Do a little research.

---

### Post by xenon3 on 2017-03-21
Thanks!!!!

Better I transfer file by USB stick from windows to UBUNTU ;)

---

### Post by TheFu on 2017-03-22
Or use network sharing if they are on the same LAN.
Or use sftp if they are on the internet.
Or use RetroShare/rsync/20 other options if you want to keep files synch'd on both systems.

There are just a few Windows-only file systems for optical storage. Almost any others will probably work. Plus, how the storage is actually mounted could matter. Can't tell from here.  I don't recall having issues with any files burned from Windows being read on Linux since around 1996, provided I didn't select some proprietary file system like UDF.

---

### Post by xenon3 on 2017-06-09
I can see AVI file now on LUBUNTU with VLC and LiVES on a laptop, but I could not see it on UBUNTU on a PC, maybe because of a by freelance hackers rebuild BIOS on the PC, BIOS did not already function correctly on PC under windows, when one migrates from windows to UBUNTU, one does not migrate the BIOS software :(

---

