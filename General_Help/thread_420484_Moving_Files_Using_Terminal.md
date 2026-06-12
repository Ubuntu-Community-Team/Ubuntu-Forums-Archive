---
title: "Moving Files Using Terminal"
date: 2007-04-23
forum: General Help
---

### Post by tomus on 2007-04-23
Basically i need to know whether you can move files in a "copy and paste" fashion somehow using the terminal, and if so what are the appropriate commands.  I have a backup file, backed up by the method shown here:

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

and I need to use it to restore my system after I managed to damage the X server.  But it says I need to place the backup file in the root partition before issuing the restore command. 

Any help very much appreciated

---

### Post by Jussi Kukkonen on 2007-04-23
```
cp /full/path/to/backup.tgz /
```
That'll copy backup.tgz to / (aka root). Just replace the path with the correct one.

Just a note: if you've just messed with xorg.conf, you don't need to restore the whole partition...

---

