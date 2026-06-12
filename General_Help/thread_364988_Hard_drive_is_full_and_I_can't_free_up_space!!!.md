---
title: "Hard drive is full and I can't free up space!!!"
date: 2007-02-18
forum: General Help
---

### Post by daxdog on 2007-02-18
So I am trying to create a DVD for the first time and having issues.  My main problem right now is that my hard drive is full.  I deleted a bunch of files and my hard drive is still full.  I get an error when I try to empty the trash folder stating:

"Could not read /home/george/.local/share/Trashinfo/DVD.trashinfo."

If you open the trash folder, there is nothing in there.  What can I do?

---

### Post by taurus on 2007-02-18
Have you look in ~/.Trash?

Applications -> Accessories -> Terminal
```
cd ~/.Trash
ls -la
rm *
sudo aptitude clean
df -h
```

---

### Post by daxdog on 2007-02-18
Hey, that got it.  Thanks!!!

---

### Post by dcstar on 2007-02-18
> **taurus said:**
> Have you look in ~/.Trash?

Applications -> Accessories -> Terminal
```
cd ~/.Trash
ls -la
**rm ***
sudo aptitude clean
df -h
```

Is it just me, or does that have the potential for disaster (if the inexperienced user doesn't cd to the correct directory)?

Perhaps it would be better to always have it thus:
```
**rm ~/.Trash/***
```
Then such dangerous commands have less chance of running in the wrong place.

---

