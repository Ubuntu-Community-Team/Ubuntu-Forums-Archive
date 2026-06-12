---
title: "(Precise) HTC One Storage Issue"
date: 2013-06-13
forum: General Help
---

### Post by HeartAttack on 2013-06-13
I recently acquired an HTC One. So far, so boring. Now, this thing has 32 GB of internal storage, with about 25 or so available to the user. But when I plug it into my computer (running on Ubuntu 12.04, which is why I'm here and not somewhere else), it for some reason believes there's only 1.6 Gigabytes, despite correctly recognising that there's well more than that saved on the phone already.... and then it freezes for a bit as though it tried dividing by zero and succeeded. How much of those 1.6 GB it claims to be free is different every time I plug it in.

In case it helps, the phone also seems to have a file system by the name of "gPhoto2".

[B]SOLUTION:

[/B]Thanks to that Mark Phelps person, I googled for something else than before... and stumbled upon this:
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)
The guide there is just about perfect, works like an absolute charm.

---

### Post by Mark Phelps on 2013-06-13
My guess is that the HTC One is running one of the newer Android versions -- ICS or JB.  Either way, you can't mount the filesystems as Mass Storage anymore as Google removed that option from the OS.

On my Samsung SGS 3, when I connect it to the PC, there is a popup allowing me to choose Multimedia device or Camera device.  Sounds like your is choosing the second by default.  You should see if you can choose the first.

---

### Post by HeartAttack on 2013-06-13
Thanks lad, while your explanation in itself didn't really help too much it did prompt me to search for the right stuff. I'll edit the solution I found into the original post and mark it solved, I suppose.

---

