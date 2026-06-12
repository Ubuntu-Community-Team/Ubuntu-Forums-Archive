---
title: "Shotwell nos starting"
date: 2012-12-30
forum: General Help
---

### Post by jotacebusta on 2012-12-30
Hi all,

I'm having trouble with shotwell, it's really strange: I cannot launch it, from the terminal I get  

:~$ shotwell

** (shotwell:6828): ERROR **: DatabaseTable.vala:92: update_version 16: [14] unable to open database file
«trap» para punto de parada/seguimiento (`core' generado)

When I launch it using sudo shotwell, everything sees right, but, of course, my photos are not there (i can get them by re building the collection).

I've tried to uninstall, reinstall... my user has all the permissions on the .shotwell directory in /home/myuser

any idea?

REgards

JC

---

### Post by xc3RnbFO8P on 2012-12-30
Try this it wont hurt :)
rename ~/.shotwell/data/**photo.db** 
to photo.dbx
and start Shotwell

---

### Post by eric-yorba on 2012-12-30
> **Ringi said:**
> Try this it wont hurt :)
rename ~/.shotwell/data/**photo.db** 
to photo.dbx
and start Shotwell

If this works, it means your database was corrupt.  Shotwell will automatically restore from the previous version of the database, so you may find some recent photos or other changes (edits, tags, etc.) are missing.

---

### Post by jotacebusta on 2013-01-01
Thank you! I changed the name of the file, as suggested, but the error message is still de same. :-(

More ideas?

---

