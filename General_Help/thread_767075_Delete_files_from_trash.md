---
title: "Delete files from trash"
date: 2008-04-25
forum: General Help
---

### Post by Sarevokphd on 2008-04-25
I'm having troubles with some files in the trash. I cannot empty the trash, cos these files where created by super user and accidentaly i deleted them as normal user. I tryed to take these files out of the trash to delete them as su with rm command in the shell but i got an error message that say I'm not allowed to move the files. And i can't even delete them from trash or empty the trash. Is there a way to empty the trash or delete those files from terminal so I can remove as su with rm, or by an other way? (i'm using Ubuntu Hardy)

Tankhs :)

---

### Post by mc4man on 2008-04-25
try using gksudo nautilus to navigate to trash and delete

---

### Post by TeoBigusGeekus on 2008-04-25
I'm on a xp machine right now, but from what I remember in Hardy, you must go to

/home/yourusername/.local/share/Trash/files

or something like this to delete them manually.

The old /home/username/.Trash folder is gone...

---

### Post by strabes on 2008-04-25
```
sudo rm ~/.local/share/Trash/files/*
```

---

### Post by Ziggy72 on 2008-04-25
This has been a pain for me too from time to time.“Conventional wisdom” (ie posts by Linux geeks) recommends a command line fix:
```
rm -rf ~/.Trash/*
```

In several cases I've found that this fails miserably. What I've done, which works, is to:
Open nautilus as root.
Navigate to /home/<your username>/.local/share/Trash/files.
Move the offending file(s) out of there into Trash (ie the root Trash).
Navigate to the root Trash and delete it/them for good.

I hope that works for you.

---

### Post by Sarevokphd on 2008-04-26
It worked :D Thank you very much all :D

I've deleted from terminal as super user the files in /home/<username>/.local/share/Trash/files, and now the trash is finally empty :D

---

### Post by Diabolis on 2008-04-27
> **Ziggy72 said:**
> This has been a pain for me too from time to time.“Conventional wisdom” (ie posts by Linux geeks) recommends a command line fix:
```
rm -rf ~/.Trash/*
```

In several cases I've found that this fails miserably.

It wouldn't work because the files that were in the trash folder were created by root. What you have to do is give root privileges to the command.
```
sudo rm -rf ~/.Trash/*
```

---

