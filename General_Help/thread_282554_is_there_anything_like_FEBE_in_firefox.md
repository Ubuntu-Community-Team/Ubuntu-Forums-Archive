---
title: "is there anything like FEBE in firefox"
date: 2006-10-22
forum: General Help
---

### Post by cnhzcy14 on 2006-10-22
i mean, every time when i reinstall ubuntu, i first remove some packages, than add backup source.list and font.conf or something else,than i update my system, at last i install some packages. i just wanna make all these easer! is there anyway?

---

### Post by ciscosurfer on 2006-10-23
You can download a program from the repos called simplebackup (you must enable your universe repository first)  You can either do this from Software Properties or you can use a terminal and (after you've enabled your universe repo ([https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html))
) you can issue the following in a terminal to grab simplebackup```
sudo aptitude update
sudo aptitude install simplebackup
```You can run the program from the command line by typing in simplebackup or go to your System menu > Administration > Simple backup config / simple backup restore

---

