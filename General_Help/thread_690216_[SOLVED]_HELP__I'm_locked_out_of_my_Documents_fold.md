---
title: "[SOLVED] HELP:  I'm locked out of my Documents folder"
date: 2008-02-07
forum: General Help
---

### Post by tr333 on 2008-02-07
I can't seem to access any files inside subfolders of my Documents folder.  When I try to open a file (eg. a txt file) it displays a message saying
> Couldn't display "/home/tom/Documents/markov/markov.pl"
The attempt to login failed.
How can I get my Documents files back to normal?

```
tom@tom-laptop:~/Documents$ ls -l markov/
total 0
?--------- ? ? ? ?                ? markov/markov.pl
?--------- ? ? ? ?                ? markov/markov.pl~
?--------- ? ? ? ?                ? markov/markov.pl.bak
?--------- ? ? ? ?                ? markov/text

```

---

### Post by danwood76 on 2008-02-07
in your home folder what is displayed when you do:
```
ls -l | grep 'Documents'
```
It might be the permissions of the folder is messed up.

---

### Post by tr333 on 2008-02-07
```
tom@tom-laptop:~$ ls -l | grep 'Documents'
drwxr-xr-x  19 tom tom      4096 2008-02-07 23:59 Documents

```

I don't think that is the problem, since I can access the files directly in the Documents folder.  It's the files inside subfolders of the Documents folder that I can't access.

---

### Post by tr333 on 2008-02-07
I think you were right.  I seem to have accidentally removed the execute permissions from the subfolders. :oops:

Seems to be all fixed now.

---

### Post by danwood76 on 2008-02-08
> **tr333 said:**
> I think you were right.  I seem to have accidentally removed the execute permissions from the subfolders. :oops:

Seems to be all fixed now.

Glad to see you got it fixed!

---

