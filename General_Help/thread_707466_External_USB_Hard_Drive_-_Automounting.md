---
title: "External USB Hard Drive - Automounting"
date: 2008-02-25
forum: General Help
---

### Post by gnelson on 2008-02-25
I have an external USB hard disk that I use to back up my Ubuntu system.  I ran into the following problem:

Every time I connect the USB drive to my PC, it automounts but assigns a different name.  The first time I used it it was "disk", then "disk-1", "disk-2", etc.  I just saw this as a minor annoyance until one time it reached "disk-6".  I then realized that mounts, even prior ones, seem to take up space in the filesystem.  I received an alert that my hard drive was full.  After some research, I found that /media/disk-1, /media/disk-2, /media/disk-3, etc.  were taking up the space.

I deleted these and recovered the space, but is there a way to prevent this from happening again?

Also, is that the normal behaviour in Linux for mounted filesystems to take space where they are mounted?  It seems odd ...

---

### Post by taurus on 2008-02-25
Did you actually unmount your external harddrive each time before you unplugged it from your machine?

---

### Post by gnelson on 2008-02-25
> **taurus said:**
> Did you actually unmount your external harddrive each time before you unplugged it from your machine?

Yes, by right click --> "Unmount Volume"

---

### Post by gnelson on 2008-02-26
Any ideas??

---

