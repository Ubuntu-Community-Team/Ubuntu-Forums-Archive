---
title: "Flash drive wont delete or import files"
date: 2007-01-25
forum: General Help
---

### Post by BWF89 on 2007-01-25
I use my 2GB PNY flash drive to move files between my iMac and PC. For about a month now it's worked perfectly. But now all of a sudden.

When I try to import a file onto it I get:
```
Could not move folder /media/USB20FD/filename
```
When I try to delete something I get:
```
Could not write to file/media/USB20FD/.Trash-1000/info/filename.trash.info
```

I've had no problems exporting files from it.

---

### Post by bodhi.zazen on 2007-01-25
There would not happen to be one of those fancy buttons on the side that slides to make it read only would there ?

---

### Post by dcstar on 2007-01-25
> **BWF89 said:**
> I use my 2GB PNY flash drive to move files between my iMac and PC. For about a month now it's worked perfectly. But now all of a sudden.

When I try to import a file onto it I get:
```
Could not move folder /media/USB20FD/filename
```
When I try to delete something I get:
```
Could not write to file/media/USB20FD/.Trash-1000/info/filename.trash.info
```

I've had no problems exporting files from it.

Apparently when "deleting" files from these things, they are not actually deleted, just moved to the Trash folder.

You may want to either empty the Trash, or manually delete the files from the (hidden) trash folder(s).

---

### Post by BWF89 on 2007-02-01
> **bodhi.zazen said:**
> There would not happen to be one of those fancy buttons on the side that slides to make it read only would there ?
Mine doesn't have one.
> **dcstar said:**
> Apparently when "deleting" files from these things, they are not actually deleted, just moved to the Trash folder. You may want to either empty the Trash, or manually delete the files from the (hidden) trash folder(s).
How do you delete files from my hidden trash folder. I didn't even know I had one.

Also theres one folder on there that won't delete. When I put it into my Macintosh the file shows up with a lock next to the folder icon. How do I delete this? Or if I can't delete it how do you format a flash drive on Linux or Mac?

---

### Post by L2wis on 2007-02-01
I had this problem! I think when you're in ur removable media you click properties and then view hidden files or something.

---

### Post by BWF89 on 2007-02-03
Nevermind I figured it out myself using Mac Disc Utility.

One more question though. When you format the flash drive it gives you different options on what file system you want to use:

Mac OS Extended (Journaled)
Mac OS Extended
Mac OS Extended (Case-sensitive, Journaled)
Mac OS Extended (Case-sensative)
MS-DOS File System
MS-DOS File System (FAT16)
UNIX File System

I formatted it the way it was defaultly formatted, as a Ms-Dos FAT16 file system. Could I format it as a Unix File System and still be able to use my data on Macintosh, Linux, and Windows machines? Or is Fat16 my only option if I want to use it on all 3? I'd try it myself  but I don't have a Windows computer at my house.

---

