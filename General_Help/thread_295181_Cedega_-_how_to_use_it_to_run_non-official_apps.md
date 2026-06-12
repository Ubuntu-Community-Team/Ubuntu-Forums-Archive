---
title: "Cedega - how to use it to run non-official apps"
date: 2006-11-07
forum: General Help
---

### Post by Tommerz on 2006-11-07
Hey :)

Does anyone happen to know how to use cedega to run non-official apps? I want to try run a few games without having to run installers, anyone know a way to just give a directory and/or .exe file to cedega and have it try to run the .exe file?

---

### Post by Perfect Storm on 2006-11-07
Try with:
cedega <path>.exe

You can get more information with:
```
man cedega
cedega --help
```

---

### Post by Tommerz on 2006-11-08
Hmm, just seems to come up with an "unscriptable object" error message :(

---

### Post by Perfect Storm on 2006-11-08
How did you install Cedega, cedegaCVS or pay Cedega? If cedegaCVS it could be that it isn't properly installed or the help files didn't come with cedegaCVS.

---

### Post by justin whitaker on 2006-11-08
> **Tommerz said:**
> Hey :)

Does anyone happen to know how to use cedega to run non-official apps? I want to try run a few games without having to run installers, anyone know a way to just give a directory and/or .exe file to cedega and have it try to run the .exe file?

Sure. 

Open up a terminal, and run the exe via cedega appname.exe. I do that to run mod installs for UT2004 and HL/HL2. 

I assume you have a windows partition that you are trying to run the games from. Keep in mind that command lining cedega with applications another partition does not always work: you may need to drag the files to the linux partition to get it to run.

---

### Post by Tommerz on 2006-11-09
Hmm, that's probably the problem, I've been trying to run them on another separate partition, using folders with many spaces (eg: /media/hda1/Documents and Settings/Captain Poo/My Documents/Apps/Baked Potatoes Emulator/potatoebakeo.exe)

Guess I'll just have to put things on the ext3 partition (or symlink :) )

Thanks!!

---

