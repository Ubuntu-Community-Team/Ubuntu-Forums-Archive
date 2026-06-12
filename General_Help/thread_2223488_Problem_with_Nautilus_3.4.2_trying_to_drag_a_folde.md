---
title: "Problem with Nautilus 3.4.2 trying to drag a folder from remote machine to my desktop"
date: 2014-05-11
forum: General Help
---

### Post by desconocido on 2014-05-11
Problem with Nautilus 3.4.2 trying to drag a folder from a remote machine to my desktop using Ubuntu 12.04.

The folder "images" contains 10 jpg files and a folder "icons". "icons" contains 12 graphics files. No hidden files. Looking at the properties of the folder, it says "23 items, totalling 347.2 kB".
folders in remote are drwxr-xr-x
files in remote are -rw-r--r--

I drag folder "images" to Desktop.

File operation dialogue box says 'Copying file 1 of 24 (in "images") to "Desktop"' 
(That should be 23 files, surely?)

Nothing happens.
Hitting cancel does not work.

After I get bored (five, ten minutes?), I close File operation dialogue box by clicking on x and look at desktop.
2 files in 1 folder "icons" in images have been copied only.

Copying multiple files in "images" and "icons" (by selecting all the files and dragging them) works ok and I get all 23 items on my desktop.

The reverse, copying "images" from Desktop to somewhere else on the same server works ok.
The reverse, copying "images" from Desktop to the original place on the same server works ok.

Delete folder "images" in Desktop; drag folder "images" from remote to Desktop:
I get the original problem again.

Maybe worth also mentioning that I get the slowdown problem with Nautilus mentioned elsewhere on the forum e.g.
[http://ubuntuforums.org/showthread.php?t=2156298&highlight=slow+nautilus+12.04](http://ubuntuforums.org/showthread.php?t=2156298&highlight=slow+nautilus+12.04)

Any suggestions would be appreciated.

P.S. Should have added tags nautilus, 3.4.2, ftp, 12.04

---

