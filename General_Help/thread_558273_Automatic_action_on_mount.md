---
title: "Automatic action on mount"
date: 2007-09-23
forum: General Help
---

### Post by viraptor on 2007-09-23
Hey
How can I make a script that will run after mounting an external disk?
I.e. I want to do `mount --bind /mnt/external/Music /home/login/Music` after I plug it in and /mnt/external is mounted
.
Any ideas apart from writing my own inode monitor for /mnt/external? I'd rather do it with a bash script.

---

### Post by musafirah on 2007-09-23
did you check system > preferences > removable drives and media if the mount choices are selected?

---

### Post by viraptor on 2007-09-23
Selected? My external disk is mounted without problems after connecting. I just want to get specific bindings working and there's no general "after connection" script available. Only "after cd inserted" / "... camera connected" and such.
I need one for standard external disk.

---

