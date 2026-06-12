---
title: "Hidden file on my system eating up disk space..."
date: 2008-03-06
forum: General Help
---

### Post by PietreWitobi on 2008-03-06
~/.cache/tracker/
   email-contents.db      (2.2 MB)
   email-index.db           (5.7 MB)
   email-meta.db            (3.0 MB)
   file-contents.db         (8.7 MB)
   file-index.db               (2.0 GB)
   file-meta.db                (36.2 GB)
   file-update-index.db   (1.1 MB)


I'm reasonably sure that it's malicious, but *what* is it?  And can I just delete it?

How do I find out what's modifying these files and kill it?

Also, this is on a /home partition of < 70 GB.

---

### Post by luisromangz on 2008-03-06
It doesn't seem to be malicious, but just the tracker indexing software databases. Although those are incredibly large files...

---

### Post by PietreWitobi on 2008-03-06
Huh.  Well, it seems to be growing to match the empty space on my Hard drive.

---

### Post by aashay on 2008-03-06
Try turning off Indexing and watching in System->Prefs->Indexing prefs

---

### Post by robertchahine on 2008-03-06
try to delete it and keep it in recycle bin. if the system worked wrong then restore them.

---

### Post by PietreWitobi on 2008-03-06
Well, I deleted it and my system seems to be running just fine.  We'll see if it comes back.

---

### Post by mallow on 2008-04-27
and my ~/.cache/tracker/ is now 21 GB 
there`s something wrong with this tracker tool

---

