---
title: "Cant Delete Two Randomly Created Folders In /media/xxxxx"
date: 2015-05-01
forum: General Help
---

### Post by jooge on 2015-05-01
I recently safely removed a USB drive from my computer and was then left with a folder: /media/xxxxxx/5ab38f02-0e59-4507-a9f9-1c3906bf2b59. Then last night I ejected a CDRom from my computer and was left with folder: /media/xxxxxx/5ab38f02-0e59-4507-a9f9-1c3906bf2b591.

[[IMG]http://7.t.imgbox.com/9sUm0jNV.jpg[/IMG]]("http://imgbox.com/9sUm0jNV")

I can't seem to delete them or remove then in any way. What are these and what can I do about it? Is there going to be a new one of these folders created every time that I remove a removable media device? Thanks in advance.

---

### Post by speartip on 2015-05-02
You will need to mount the media that created the folder first. Then it should delete.
If that doesn't work try with the media mounted, deleting them as root.
```
[COLOR=#111111][FONT=Consolas]sudo rm -r -f [/FONT][/COLOR][COLOR=#000000]/media/xxxxxx/5ab38f02-0e59-4507-a9f9-1c3906bf2b59[/COLOR]
```
Be careful using this command though, & make sure there is nothing in that folder that you need.

---

### Post by jooge on 2015-05-30
Excellent! Thanks **speartip**. Worked like a charm. Sorry about the really late response.

---

### Post by Keith_Helms on 2015-05-31
How did you "eject" the media?  If you just pressed the eject button on the drive, the system may still think it's mounted and the mount point may continue to exist.  Click on file manager or places or whatever is on your flavor of ubuntu and get the list of all mounted drives and partitions.  Right click on the media and select eject in order to properly remove it from your system.

---

### Post by jooge on 2015-05-31
Keith, I did right click on the device from the left panel in Nautilus and press eject.

---

