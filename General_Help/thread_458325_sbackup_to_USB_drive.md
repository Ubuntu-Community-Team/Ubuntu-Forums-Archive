---
title: "sbackup to USB drive"
date: 2007-05-29
forum: General Help
---

### Post by griffithc on 2007-05-29
I'm using sbackup, but I want to backup  to a USB drive rather than to my Ubuntu partition. Has anyone managed to do this? Has anyone had success with any other GUI backup package in Linux?

---

### Post by reclusivemonkey on 2007-05-30
> **griffithc said:**
> I'm using sbackup, but I want to backup  to a USB drive rather than to my Ubuntu partition. Has anyone managed to do this? Has anyone had success with any other GUI backup package in Linux?

I use the CLI (a script calls rsync), but there is a GUI for rsync called grsync I think.

---

### Post by cward002 on 2007-05-30
Yes I do this as well. It is just a matter of figuring out the mount point for your USB disk and selecting that as the place wher you want sbackup to store backups. For me the mount point is /media/disk

---

### Post by griffithc on 2007-06-02
Thanks, it worked well!

---

### Post by cward002 on 2007-06-02
Glad it worked!!!

---

### Post by russell.h on 2007-06-24
I'm messing with this right now, and it appears to be "working", but whenever I go to remove the usb stick it pops up a message saying that I need to wait a minute while it writes stuff to the drive. I'm not sure, but it seems to me like it is just storing all the changes somewhere temporary until I unmount the thing, at which point it actually writes it to the drive. But that doesn't do me much good if the point is to back up.

Would someone who knows what they are talking about (in other words someone other than myself) care to comment?

---

