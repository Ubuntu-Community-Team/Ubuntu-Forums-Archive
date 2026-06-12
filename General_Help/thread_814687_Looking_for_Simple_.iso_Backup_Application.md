---
title: "Looking for Simple .iso Backup Application"
date: 2008-05-31
forum: General Help
---

### Post by monsieurdozier on 2008-05-31
Hey,

I'm looking for a very simple application to make direct .iso backups of my driver cds dvds, etc.  

I'm new to the whole .iso making process, so if there is a program that has a "Make .iso from this CD/DVD" button, I would be thrilled.

-Monsieurdozier

---

### Post by quelx on 2008-05-31
open a terminal

```
dd if=/dev/cdrom of=~/Desktop/mycdimage.iso
```

---

### Post by elmer_42 on 2008-05-31
While searching for a quick beginner's guide to dd, I found an [old topic]("http://ubuntuforums.org/showthread.php?t=137931") that contained this wonderful answer by daredevil:
> **daredevil said:**
> Found this in tips and tricks section

Open up a terminal window into this window type: dd if=/dev/cdrom of=$HOME/cdrom_image.iso

I'll now explain what this all means in the key below

dd - disk duplicate
if - input file
of- output file
$HOME - system variable that points to your user directory.

Ps:Change cdrom_image to what ever you want the iso to be called.

---

### Post by monsieurdozier on 2008-06-01
Thanks guys, this'll work perfectly.

---

### Post by OliverW on 2008-06-01
> **monsieurdozier said:**
> Hey,

I'm looking for a very simple application to make direct .iso backups of my driver cds dvds, etc.  

I'm new to the whole .iso making process, so if there is a program that has a "Make .iso from this CD/DVD" button, I would be thrilled.

-Monsieurdozier

The Ubuntu standard burning application 'Brasero' (you can find that under Applications > Sound & Video) has an option to 'Copy a disc' either to another CD/DVD or to an image file (.ISO).

---

