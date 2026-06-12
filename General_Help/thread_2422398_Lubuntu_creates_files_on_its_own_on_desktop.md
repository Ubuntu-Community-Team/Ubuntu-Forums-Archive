---
title: "Lubuntu creates files on its own on desktop"
date: 2019-07-07
forum: General Help
---

### Post by zaisen on 2019-07-07
Dear Ubuntu-Community,

I'm new with lubuntu and actually try to learn the basics step by step. But here is a behavior I can't explain. 

Lubuntu sometimes likes to create files with random names by itself if I shutdown my computer and displays them on desktop after I restarted it. I made a screenshot to show the issue. 

[ATTACH=CONFIG]283572[/ATTACH]


I hope you can help me to understand it. Thanks in advance.

---

### Post by GhX6GZMB on 2019-07-09
I have the same issue (Lubuntu 19.04) and would like to understand as well.

Thank You.

---

### Post by #&amp;thj^% on 2019-07-09
[https://github.com/lxqt/pcmanfm-qt/issues/944](https://github.com/lxqt/pcmanfm-qt/issues/944)

---

### Post by ajgreeny on 2019-07-09
Never seen this and I do not know Lubuntu any more now it's moved to the lxQt DE, but have you opened or at least tried to open one of those files to see what it contains?

You can also use command ```
file Desktop/filename
``` and show us the output here; I guess form the names they are .desktop files (launchers for applications) renamed by something so try opening one with a **right click -> Open with** and use whatever text editor Lubuntu now uses.

EDIT:
Too slow and ninja'd by 1fallen.

---

### Post by GhX6GZMB on 2019-07-09
Yep, 1fallen has it nailed. The files/icons have a content of 0 bytes.

---

