---
title: "How to save GParted screenshot?"
date: 2006-12-05
forum: General Help
---

### Post by Bartender on 2006-12-05
The GParted LiveCD has a screenshot function.  The little icon to the left of the life preserver in the lower right corner of screen.  How the heck do you save that screenshot once you've exited GParted?  I've tried several things but none have worked so far.  It'll save the .jpeg, then you can open Thunar and find the .jpg.  I tried saving it in "tmp" folder, but it appeared to be gone after exiting GParted and rebooting.

---

### Post by Dubbayoo on 2006-12-05
save it to a different disk. The tmp folder would obviously be on a non-writable cd or in memory only.

---

### Post by rsambuca on 2006-12-05
I think you will have to mount one of your drives and transfer the file to there.

---

### Post by Bartender on 2006-12-05
Thanks, guys.  Found an easier way to do it.  Ran an Ubuntu LiveCD instead of the GParted LiveCD.  Started Gnome Partition Tool.  With the map on the screen, went to "Take Screenshot" (Applications>Accessories>Take Screenshot).  Saved it to desktop, (you have to specify an extension as part of the name; I used .png but maybe you could use .jpg?) then went to the icon on the desktop and saved it to a thumbdrive.
It's harder from the GParted LiveCD.

---

### Post by Bartender on 2006-12-25
I think I've got an answer on this - it was right there in a GParted LivedCD (GPLCD) Forum sticky. 

[http://gparted-forum.surf4.info/viewtopic.php?id=191](http://gparted-forum.surf4.info/viewtopic.php?id=191)

After following his directions I can see my USB thumbdrive by opening Thunar File Manager (along the bottom of the screen in GPLCD) and going in to 'tmp'.  Cut the screenshot from 'root' and Paste it into 'tmp/usb'
You have to rename the screenshot if you're doing more than one, otherwise the next screenshot will try to overwrite the first.

---

