---
title: "Compiling a .tar.bz2 with a .patch2 file."
date: 2006-11-17
forum: General Help
---

### Post by nagorB on 2006-11-17
Hello Ubuntu Forums. I searched the site for a while and I couldn't find a solution to my problem, so I decided to join so that I may ask in the flesh. I hope all of you smart people will be able to assist me. 

Anway, my problem comes from me trying to install a program called *ONScripter* from its source with a patch. Now, ONScripter is available in the repositories, but the patch only works with a specific build from nscripter.insani.org. The patch is a *.patch2* file, which doesn't seem to be very common. I am having problems applying this patch to ONScripter before I configure and make install, etc.

**Here's the breakdown on how I did things. Perhaps somebody can tell me what I did wrong:**
1.) I downloaded the [latest build of ONScripter](http://nscripter.insani.org/onscripter.html).
2.) I extracted it.
```
tar -xvf onscripter-20060724-insani.linux.tar.bz2
```
3.) I downloaded [the patch](http://haven.parodius.com/stuff/onscripter-20060724-insani-zalas.patch2).
4.) I cd'd to the source directory of the untar'd ONScripter.
5.) I attempted to patch the program in the directory, simply called 'onscripter' using information from other patching tutorials I found.
```
patch -p1 </home/USERNAME/Games/Onscripter/onscripter-20060724-insani-zalas.patch2
```
...which returned this message:
```
can't find file to patch at input line 6
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Only in onscripter-20060724-insani-zalas: Makefile
|Only in onscripter-20060724-insani-zalas: Makefile.Linux.vignette
|diff -au onscripter-20060724-insani/NsaReader.cpp onscripter-20060724-insani-zalas/NsaReader.cpp
|--- onscripter-20060724-insani/NsaReader.cpp   2006-06-18 10:35:28.000000000 -0700
|+++ onscripter-20060724-insani-zalas/NsaReader.cpp     2006-10-24 14:27:20.000000000 -0700
--------------------------
File to patch:
```

So I input */home/USERNAME/Games/Onscripter/onscripter-20060724-insani.linux/onscripter* as the 'File to patch'

...which gave me:
```
patching file /home/USERNAME/Games/Onscripter/onscripter-20060724-insani.linux/onscripter
Hunk #1 FAILED at 47.
Hunk #2 FAILED at 115.
Hunk #3 FAILED at 142.
Hunk #4 FAILED at 166.
Hunk #5 FAILED at 183.
5 out of 5 hunks FAILED -- saving rejects to file /home/USERNAME/Games/Onscripter/onscripter-20060724-insani.linux/onscripter.rej
can't find file to patch at input line 114
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -au onscripter-20060724-insani/NsaReader.h onscripter-20060724-insani-zalas/NsaReader.h
|--- onscripter-20060724-insani/NsaReader.h     2006-06-18 10:35:28.000000000 -0700
|+++ onscripter-20060724-insani-zalas/NsaReader.h       2006-10-24 14:18:54.000000000 -0700
--------------------------
```

I have tried various 'p' options, such as '-p1', '-p0', etc and none of them work. Also, none of the threads about patching contain anything about *.patch2* files.

So I ask you all, does anybody have any idea how to use a .patch2 file and know what I am doing wrong?

Thank you.

---

### Post by loell on 2006-11-17
either there is a prior patch that is needed perhaps .patch1 before patch2 is applied, or patch2 is not a correctly written patch.

---

### Post by nagorB on 2006-11-17
From what I have heard on the group's IRC channel, the patch I was linked to is the only one that is required. In fact a few other people have already applied this patch correctly, but none of them were around, so I couldn't ask them.

So does the '2' in '.patch2' imply that a '.patch1' is required somehow?

---

### Post by loell on 2006-11-17
yes probably, from the errors that you posted, the patch seems to expect strings or lines of code that is not there.

---

### Post by nagorB on 2006-11-17
> **loell said:**
> yes probably, from the errors that you posted, the patch seems to expect strings or lines of code that is not there.

Ok. Thanks. I'll check things out with the IRC people.

[SIZE="1"]...or just wait until the group releases an official translation of the game for Linux, which would allow me to use the regular ONScript package.[/SIZE]

---

