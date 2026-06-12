---
title: "Trying to install AutoTalent"
date: 2018-11-18
forum: General Help
---

### Post by bappobappo on 2018-11-18
I've done all the steps from the video [https://www.youtube.com/watch?v=mQcKFKAfylQ](https://www.youtube.com/watch?v=mQcKFKAfylQ)

I've done every step correctly, but when I get to "sudo cp autotalent/lib/ladspa" (im using the 32 bit) I get a message saying

"cp: missing destination file operand after 'autotalent/lib/ladspa'Try 'cp --help' for more information."

I'm trying to get AutoTalent for Audacity but I can't due to this.
Also fairly new to Ubuntu.
Thanks

---

### Post by TheFu on 2018-11-18
The cp command requires 2 arguments.
You've only provided 1 above.  That is what the error is telling you.

A free beginner Linux course will teach cp, probably in the first lesson.

From the manpage for cp:
```
NAME
       cp - copy files and directories

SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... DIRECTORY
       cp [OPTION]... -t DIRECTORY SOURCE...

DESCRIPTION
       Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.
```

Most people use 
```
       cp  SOURCE  DEST
```
where SOURCE is either a directory or some sort of regex pattern 
and
DEST is the target directory.

---

