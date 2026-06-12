---
title: "xubuntu trash help"
date: 2007-01-12
forum: General Help
---

### Post by tjotser on 2007-01-12
Hi there. I have a computer with a 12GB and a 30GB harddisk in it. The 12GB is my xubuntu partition. Now the problem is, i have this 9GB rar-file (on the 30GB)from a download which never finished and when i want to delete it tries to move it into the trash. The trash-folder is located on my 12GB so it just stops, and the file remains..

Is there anyway to skip this "keep-trash" function ,OR just to get rid of this one file with a terminal command or something?  Thanks in advance :KS

---

### Post by NeoLithium on 2007-01-12
```

sudo rm /path/to/file/filename.rar

```
Just make sure you're careful to have the exact filename so you don't delete anything else by accident. That should bypass the trash and remove it for you.

---

### Post by tjotser on 2007-01-12
Thank you, I was expecting something tricky and forgot all about that command. Had a long day at work i guess.. thanks for taking the time !!:D

---

### Post by NeoLithium on 2007-01-12
No problemo :)

---

