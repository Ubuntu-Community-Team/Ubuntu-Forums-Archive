---
title: "Mp3gain on files on NTFS drive?"
date: 2008-06-06
forum: General Help
---

### Post by Juleshu on 2008-06-06
I'm using mp3gain. 
This command:  find . -name *mp3 -exec mp3gain -a -k {} \
will normalize the volume on all of my mp3s on my linux partition.
Is there a way to modify the find command so that mp3gain will run on all of the files I have on my NTSF windows partition (/dev/sda1)?


thanks

---

### Post by Juleshu on 2008-07-05
> **Juleshu said:**
> I'm using mp3gain. 
This command:  find . -name *mp3 -exec mp3gain -a -k {} \
will normalize the volume on all of my mp3s on my linux partition.
Is there a way to modify the find command so that mp3gain will run on all of the files I have on my NTSF windows partition (/dev/sda1)?


thanks

Bump

---

### Post by eriqjaffe on 2008-07-05
Unless I'm off, all you should need to do is mount /dev/sda1, navigate to it, and run that command.

---

