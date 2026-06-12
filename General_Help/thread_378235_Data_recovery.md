---
title: "Data recovery"
date: 2007-03-07
forum: General Help
---

### Post by uNiverSus on 2007-03-07
Hi , i really need a program which is able to recover my data. My lil sister deleted yesterday , all movies , music , and my PHOTOGRAPHS !! Is there any good program ?
plz help . Thanks in advance
PS.Sry for ym very bad english

---

### Post by nicker2005 on 2007-03-07
you can try:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

or 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good Luck!

---

### Post by bapoumba on 2007-03-07
@ uNiverSus: I've moved your thread to the "General Help" forum.

---

### Post by uNiverSus on 2007-03-07
Ok it works very fine . Thanks ;)

Got just one question to all PhotoRec user ! Can photorec recover .avi files ??

---

### Post by joeyteetops on 2007-12-21
Unlikely to be able to do so as those avi files have a higher propensity to be more fragmented and most RAW-style recovery software won't be able to do anything.   Photos have a better chance because they are smaller, typically not fragmented (or you'd lose them when you lost the file related inodes), and they actually usually have nice attributes within the binary itself that help define the file.  (like the date the file was taken, etc) 

Hope that helps someone in a similar situation.  If you ever get confused I'd give a call or email to the guys at Gillware if you are shopping for professional [data recovery]("http://www.gillware.com").  Their linux file system pricing ain't that great but if you are ever in a massive pinch their expertise can be very useful.

---

### Post by az on 2007-12-21
Foremost and photorec can rescue avi files.  I don't think they will be significantly fragmented unless your drive was really full.

Stop using your computer immediately.

You can also make an image of all the unallocated blocks (blocks with deleted data) and file-carve the avis out of that image.  Use dls from the sleuthkit for that.  Use a live cd like ubuntu-rescue-remix for that.  You don't want to be installing any software on that drive until you recover your data.

---

