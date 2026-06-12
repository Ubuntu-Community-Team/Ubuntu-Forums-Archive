---
title: "Bacula Restore Question"
date: 2008-04-25
forum: General Help
---

### Post by Griff on 2008-04-25
[SOLVED: SEE SECOND POST]

I had to format my / but bacula volume (Volume001) was on /storage.  I need to specify this volume to be used.  How do I use this volume when I'm in bconsole?  My .conf files are all the same, but I still can't restore from this volume without doing something.

Thanks,
Griff

---

### Post by Griff on 2008-04-26
Found the way and so to help others:

If a volume record is no longer present in the database you need to recreate it.  So if you have a bacula-sd.conf in ~/bacula and a volume BacBackups /storage you need to run bscan:

bscan -s -m -c ~/bacula/bacula-sd.conf -v -V BacBackups /storage

-Griff

---

