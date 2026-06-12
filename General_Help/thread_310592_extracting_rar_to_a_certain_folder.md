---
title: "extracting rar to a certain folder"
date: 2006-12-01
forum: General Help
---

### Post by Lukich on 2006-12-01
Hi.  I was wondering how can I extract my rar achive into a certain folder.  unrar e filename.rar simply extracts them to a current directory.  I don't think there's anything on it in the manual.  Is it possible?
Thanks a lot!

---

### Post by styracosaurus on 2006-12-01
You could move the rar archive into the directory you want and then unrar it?

---

### Post by LLRNR on 2006-12-01
First, **cd** to the dir that contains your .rar file. (Let's assume it's called "archive.rar".) Then:
```
rar x archive.rar /path/to/desired/folder/
```

LLRNR

EDIT - For me that works... I installed "rar" with *sudo aptitude install rar* :D

---

### Post by Lukich on 2006-12-01
LLRNR, didn't really work for me.  I did install rar the same way you did.  However, I want to unrar it, not rar it, besides switch x, according to the manual means "exclude specified file".

---

### Post by LLRNR on 2006-12-01
:D not quite right... **x** without anything near him means, according to **rar --help**:
> x             Extract files with full path
If you DID install "rar" with "aptitude", then it should work.

I did a test myself and it works... anyway, in the */path/to/desired/folder/* above, "folder" has to exist already.

LLRNR

---

### Post by Lukich on 2006-12-01
What I did is to try and owerwrite the installation I did with Automatix with the aptitude one.  I think it didn't work because the help file tells me different things about x.  I guess I should try to remove rar before installing it with aptitude.  It sucks, though, that you have to create a directory first, but I guess it's not suh a big deal.  Thanks!

---

### Post by LLRNR on 2006-12-01
I didn't install *rar* with Automatix for the simple reason that I refused to use Automatix from the very beginning, and the most natural thing for me was to use "*sudo aptitude install rar*". You're right, the package installed by Automatix might be a different one than the one I got with aptitude.

Making a new folder, also, shouldn't be too much of a hassle, you'd just have to **cd** to the directory which will hold the new one and then enter ```
mkdir NameOfFolder
```

LLRNR

---

### Post by Lukich on 2006-12-01
Here's another thing I didn't do right - I didn't specify the full path, instead of doing /home/me/music/folder I tried to type in folder and that didn't work.  Everything's fine now, thanks again!

---

