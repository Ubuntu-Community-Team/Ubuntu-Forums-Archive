---
title: "Archive Manager - unspecified error"
date: 2014-06-07
forum: General Help
---

### Post by Bewildered_Bob on 2014-06-07
Ubuntu 14.04 was apparently successfully installed despite my lack of experience (beginner's luck) but after downloading 2 pgms neither one will run. "Error occured while loading archive" isn't helpful to a newbie. What is wrong ? Thanx.

Bewildered Bob :confused:

---

### Post by Impavidus on 2014-06-07
How are you trying to download and install programs? The preferred way is through the software centre, or using synaptic, aptitude or something like that, which are more advanced. Picking software from random websites is more complicated and less secure.

Also note that Windows executables (*.exe) don't run on Linux. If it's a self-extracting zip archive the archive manager can handle it, and therefore it is started. Software called wine, a windows compatibility layer, can run some Windows executables, but don't hold your breath. It's best to find Linux alternatives.

---

### Post by Bewildered_Bob on 2014-06-08
Impavidus: THANX !!  Apparently the pgms downloaded from websites were for Windows only. Wouldn't it be helpful for the err msg to give the user a clue what went wrong ?  Even the title "archive manager" doesn't signify anything to a newbie. Apparently i have a l-o-t to learn before using Ubuntu successfully. Are there any online tutorials which help ?

Bewildered_Bob

---

### Post by Bewildered_Bob on 2014-06-12
Hello again: the pgm to be downloaded is a "system scanner" (RAM analysis) from Crucial corp. Their tech support claims that the pgm works for both Linux & Win which, if true, means that is shd have downloaded and executed successfully. If so what is the cause of the archive manager err msg ? Thanx.

Bewildered


*** UPDATE - a second tech support rep corrected the erroneous statement abt "joint" pgm for Win & Linux. Apparently the system scanner is ONLY for Win PCs.

---

### Post by sandyd on 2014-06-12
Hi, I do not think there is a version of the scanner for Linux.

If you can provide us with your computer model and the output of
```

sudo lshw -class memory
``` from the terminal, we can help your further.

---

### Post by Impavidus on 2014-06-12
Even if it works both on Windows and Linux, there will be two different executable files – one for Windows and one for Linux. Still the Windows executable file, with the .exe extension, won't run in Linux.

---

