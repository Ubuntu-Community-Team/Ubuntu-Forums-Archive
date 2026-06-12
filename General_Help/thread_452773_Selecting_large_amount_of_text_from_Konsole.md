---
title: "Selecting large amount of text from Konsole"
date: 2007-05-23
forum: General Help
---

### Post by wuhaa on 2007-05-23
Hi,

I'm using Kubuntu 7.04 on my PC. I need to select a large bunch of text (maybe 2000 lines or so). Is there an easier way then sitting here and trying to scroll the mouse with left click held.

Usually I will just use the mouse but sometimes its just takes way too long.

Thanks,

---

### Post by deeZee on 2007-05-23
Hi, there.  If your lines of text are the result of running a command you could redirect the output to a file like so:
```
dmesg > someFileName.txt
```where "dmesg" is the command and "someFileName.txt" is the file created in the current directory.  Then, open the file with a text editor and select all text with ctrl + a and have your way with it!  This probably isn't the most elegant way to do it, but it's all I can think of.;)

---

### Post by wuhaa on 2007-05-24
So simple

Thanks!

---

### Post by deeZee on 2007-05-24
Your welcome; but I just thought of an unintended consequence:  If the file "someFileName.txt" already exists it will be overwritten. If you want to store all of your output into a single file use the following instead:```
dmesg >> someFileName.txt
```That will append (add to the end of the file) the output of the command, instead of overwriting it.  My sincerest apologies if I caused you any inconvenience.

---

