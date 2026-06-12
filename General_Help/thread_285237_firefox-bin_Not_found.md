---
title: "firefox-bin: Not found"
date: 2006-10-26
forum: General Help
---

### Post by Sendai on 2006-10-26
With some exec files, i get a "Not found" error when i try to run them although it is present in the right directory. :
```
hig@jmc:/opt/swiftfox$ ./firefox
./run-mozilla.sh: 424: ./firefox-bin: not found
hig@jmc:/opt/swiftfox$ wine
bash: /usr/bin/wine: Aucun fichier ou répertoire de ce type
hig@jmc:/opt/swiftfox$ /home/hig/progs/flock/flock-bin
bash: /home/hig/progs/flock/flock-bin: Aucun fichier ou répertoire de ce type
hig@jmc:/opt/swiftfox$ ls /home/hig/progs/flock/flock-bin
/home/hig/progs/flock/flock-bin
hig@jmc:/opt/swiftfox$ 

```
I tried to change the permission on these files and i get the same error.

Is someone nice enough to help me, i currently have no clue where to look at.

---

### Post by jamesford on 2006-10-26
got the same prob but no solution..

---

### Post by jamesford on 2006-10-27
ah i think i found the solution. u just need some 32 bit libs
sudo apt-get install -y ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

this fixed it for me, not sure all those are needed tho

---

### Post by jasonlfunk on 2006-10-27
You should also make sure that they are flagged as executable.

sudo chmod +x firefox-bin

---

### Post by Sendai on 2006-10-27
> **jamesford said:**
> ah i think i found the solution. u just need some 32 bit libs
sudo apt-get install -y ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

this fixed it for me, not sure all those are needed thoThank you ! it fixed it for me too.
Arigato !

---

