---
title: "NTFS partition disappeared"
date: 2007-03-31
forum: General Help
---

### Post by ouff on 2007-03-31
I'm running Edgy on a laptop with an NTFS partition.  I used the NTFS-3g driver to mount my NTFS partition so I could store all my files on it and hence have access to them in windows.  Things were going great until the last time I booted up, at which time the computer decided I had mounted this drive too many times (30) without a filesystem check, and so it did one.  The scan finished normally and no errors were reported, but when I booted up, my partition was gone.  /media/hda1 still exists, but there's nothing in it.  The fstab entry looks the same as it did the last time the partition mounted properly.  I've rebooted several times and it hasn't come back.  This is the 5th or 6th problem I've had with Ubuntu changing things on me once I've gotten them set up the way I want them.  Not sure what that's all about.

Any thoughts?

---

### Post by acormack on 2007-04-01
can you access it from windows still?

---

### Post by ouff on 2007-04-01
Yes I can.

---

### Post by acormack on 2007-04-01
Use Start, System Settings, Disk & filesystems and try to mount using the gui interface

---

### Post by ouff on 2007-04-01
So it's back.  Not sure why.  But it is.

---

### Post by acormack on 2007-04-01
Glad you are working again.

if you make a copy of /etc/fstab /etc/mtab you will have the settings just in case

---

