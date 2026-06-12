---
title: "Help deleting a CD image on a  USB stick."
date: 2008-04-14
forum: General Help
---

### Post by fredmundo on 2008-04-14
Hi guys, 
First post here so please go easy on me, I've been reading a while and sorted just about all my problems with threads from here, so I'm hoping that you guys can help. 

 I recently recieved a 1GB USB stick as a freebie. It's got a company catalogue on it and some free space. The catalogue is on it as a seperate partion that I have been trying to delete to no avail.
My PC picks it up as a CD drive and mounts it (/dev/scd1) so I can read the info on it.
Every which way I have tried to delete this has failed.

I have had a good look round here and other places and eventually googled this thread which seems to be the nearest I have found to the same problem:
[http://mandrivausers.org/index.php?showtopic=42461](http://mandrivausers.org/index.php?showtopic=42461)

this links to this:
[http://mandrivausers.org/ndex.php?showtopic=41247&st=0&p=316261&#entry316261](http://mandrivausers.org/ndex.php?showtopic=41247&st=0&p=316261&#entry316261)

unfortunately I get this spat back at me:

> dd: opening `/dev/scd1': Read-only file system

I've also tried using fdisk and qtparted and nothing seems to shift it. I can do what I like with the left over 400mb or so no problems.
Any ideas?

---

### Post by forestpixie on 2008-04-14
Try doing it as root - but be careful that you're working on the right disc

Or run nautilus as root, gksudo nautilus, try reformatting it with gparted

---

### Post by fredmundo on 2008-04-14
Thanks for the reply, I've already tried doing everything as root and also tried gparted too. Both gparted and qtparted only list the portion of the drive that is not the CD image portion of the drive.
If it helps clarify, basically the USB stick is picked up as being two devices:
/dev/sdb/  (400MB)
/dev/scd1/  (CD Image)

---

### Post by forestpixie on 2008-04-14
Can you change the properties on the readonly part from root to your account? Not quite sure why it won't let you delete. Not sure I'm going to be able to help without searching the net -

---

