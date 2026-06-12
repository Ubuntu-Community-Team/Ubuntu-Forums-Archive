---
title: "Unable to mount the selected volume."
date: 2007-04-10
forum: General Help
---

### Post by Dream. on 2007-04-10
Why do I get this error on my dvd rom drive when I insert a disc and try to browse it?

DVD ROM:

Unable to mount the selected volume.

mount: not a directory

--------------------------------------------

When I go to terminal and type in:

sudo mount /media/cdrom0/ -o unhide

I get the same message:

mount: Not a directory

---

### Post by phidia on 2007-04-10
When mounting a cd from the terminal I usually do it this way
> sudo mount -t iso9660 /dev/hdX /media/cdrom0
The "X" should be the actual device # obviously.
see if that works.

---

### Post by Dream. on 2007-04-10
Thanks for your reply phidia, 

I inserted a data cd into the drive and it mounted without problems so it got me thinking a little. I went and borrowed some more dvd's to try and guess what, they work fine. I'll request this thread be deleted as it is of little benefit to the community.:lolflag:

---

