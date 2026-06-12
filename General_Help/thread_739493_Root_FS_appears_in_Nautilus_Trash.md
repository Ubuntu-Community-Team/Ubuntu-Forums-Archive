---
title: "Root FS appears in Nautilus Trash"
date: 2008-03-29
forum: General Help
---

### Post by cconroy on 2008-03-29
I went to go empty my Trash folder today and found that every folder from my root directory appears in my user's Trash display in nautilus.

Thus, if I go to :trash in Nautilus I see bin, boot, cdrom, dev, etc, home, initrd, lib, etc...

If I go into a terminal and cd into ~/.Trash/ I see an empty folder (as I have deleted everything but these)

If I gksudo nautilus, root Trash appears empty. /home/$USERNAME/.Trash/ also appears empty in Nautilus with gksudo

I've tried deleting my .nautilus folder and then launching, but the error persists.

This is all very strange. I'd like to get them out of there (as it is an annoyance when I go to empty the trash). Any thoughts?

---

### Post by DoctorMO on 2008-03-30
Have you tried removing the ~/.gnome2 directory? it sounds like the trash directory for your computer is now pointing to / and this may be a gconf setting, it's up to you if you want to go digging in gconf to see if it's there.

---

### Post by cconroy on 2008-03-30
Thanks. I nuked that directory. It didn't fix it right away, but once I logged out and back in again, it appears to be fixed.

---

