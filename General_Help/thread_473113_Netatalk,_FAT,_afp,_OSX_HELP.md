---
title: "Netatalk, FAT, afp, OSX HELP"
date: 2007-06-13
forum: General Help
---

### Post by tburgund on 2007-06-13
Power loss again:(
My main computer is MacBookPro running OSX. 
My home server is headless Ubuntu.
When I ssh from MBP terminal to ubuntu everything works fine (I can see all my files on Ubuntu).
Torrentflux works fine.
My problem is when I connect from MBP using Finder(afp://xx...)  I can't see any of my files on Ubuntu home server (something I used to without problem)
Please help
Tomica

---

### Post by macnerd on 2007-07-01
This happened to me as well.  I tried deleting DSStore files, etc.  My only way out of it was to copy the files to a separate drive, delete the directory I had problems with and then copy the files back to a newly created directory.  Not the best solution but it worked for me.

Creating a different directory on the server and moving the files didn't work, I had to copy them to another drive.  If you duplicate the files to the new directory on the same drive it might work, I didn't go that far since I had an extra drive in the server.

---

