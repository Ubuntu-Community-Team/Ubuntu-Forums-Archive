---
title: "Locked folder problem."
date: 2008-07-01
forum: General Help
---

### Post by cereal killer on 2008-07-01
I just transferred a few folders from an old CD onto my desktop, and I can't delete or move them. The files inside I can use, but can;t delete or move them either.

Help please?

---

### Post by VMC on 2008-07-01
Something along this line, using Terminal

```
sudo chown -R <your username>:<your group> <device mount path OR Folder>
```

---

### Post by soccerboy on 2008-07-01
if you go the folder, what is the output of ls -al

---

### Post by cereal killer on 2008-07-01
> **soccerboy said:**
> if you go the folder, what is the output of ls -al

I'm a very bigtime n00b, please elaborate.

---

### Post by soccerboy on 2008-07-01
cd to the folder in question in the terminal.  then type ```
ls -al
``` and press enter.  Post the entire output.  It may be easier to do ```
ls -al > ~/foldercontents.txt
``` if there are a lot of files and just post foldercontents.txt from your home directory

---

