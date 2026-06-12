---
title: "Cd Mounting Problems"
date: 2007-12-29
forum: General Help
---

### Post by techgeek40 on 2007-12-29
I have several CD's I burned with Windows vista - (zipped files and photos)
When I put them in Gutsy - it is giving me the following error:

Cannot mount volume.
Invalid mount option when attempting to mount the volume "UDF Volume'.

Any help

Wanted to add this:
The /etc/fstab listing is as follows:

/dev/scd0        /media/cdrom0    udf,iso9660 user,noauto,exec 0   0

---

### Post by disturbed1 on 2007-12-29
I've received this error before when people have handed me CDs that where burnt as multi session, but left open.

The easiest way to fix this (if that is the problem ;) ) would be to close the sessions using the same burner, and burning program the discs where originally written with.

---

### Post by techgeek40 on 2007-12-29
But, I can open those same CD's on another "windows" computer
But not on my Gutsy laptop

---

