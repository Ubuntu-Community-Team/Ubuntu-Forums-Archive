---
title: "Installed programs not being recognized and ....stuff"
date: 2008-04-19
forum: General Help
---

### Post by jluttinen on 2008-04-19
Hello all, i haven't been able to find anyone to address this problem of mine so here goes.

     I'm not exactly a noob at Linux but I'm by no means experienced. I have a problem with two programs that i've installed simply acting as if they don't exist.  To simplify trouble shooting i've moved to the directory that the program is actually in and attempted to run it via console but I simply get the error **Bash: rolaunch command not found.**  the program installed is Regnum.  I've extracted it and even attempted to compile it but can't seem to get it to work.  All the demos say that it should run with a simple double click right after extracting.  Does anyone have the slightest clue as to what's wrong and how to fix it? If this is any help also (most likely a completely seperate error) I'm also getting an error when attempting to rebuild the rpm database.  The error is: **error: cannot create transaction lock on /var/lib/rpm/__db.000**  any suggestions or knowledge would be appreciated.

p.s.: the reason I don't think this is just that one program is because I have another program that worked great before I re-installed linux and I'm getting the same **Bash: command not found** error.

---

### Post by george9233 on 2008-04-19
Maybe you should move to the folder and try 

```
./*yourprogramname*
```

---

### Post by jluttinen on 2008-04-19
crapp didn't even think about that but now I have another problem.  I got these two errors.

it gives me a memory map then (Core Dumped)

when i run it with the sudo command I get the exact same thing.  A core dump.

---

### Post by jluttinen on 2008-04-19
I figured it out, it was a setting that I had to use while using ./myprogram.  Thank you evryone for your help.  All programs now run fine.

---

