---
title: "2 commands--one alias"
date: 2007-09-29
forum: General Help
---

### Post by n.aggel on 2007-09-29
hi,

i have installed i  my system, mathematica 5.1 and i want to install mathematica 6....i know that these two packages install in different directories so there shouldn't be any problem{i 've done it on windows a thousand times}....

There is only one problem in the command shell they are  both invoked with the command ""mathematica" {i mean if you don't specify the full path to the program}..so how will the shell know which one to pick?

Is there a way to choose which command will be invoked with the alias "mathematica"??

thanks in advance for your help...

---

### Post by ddrichardson on 2007-09-29
They should be in different directories so mathematica on its on should start neither. In this case just create a symbolic link to one as say mathematica5 and another as mathematica6 in /usr/bin and you will be able to choose.
```
ln -s /opt/wherever/mathematica /usr/bin/mathematica5
```

If it creates an addition to the PATH variable to run them using the mathematica command then do the same and avoid the use of mathematica as a command.

---

### Post by Maxtorm on 2007-09-29
Another option: Use "which" to determine which executable is running by default (i.e. in the system path):
```
which mathematica
```
Then modify your ~/.bashrc file to include an alias that points to the non-default executable. For instance, assume Mathematica 5 is the executable that runs by default and the Mathematica 6 executable is located in /usr/bin/mathematica6. Add a line to .bashrc at the end similar to
```
alias mathematica6='/usr/bin/mathematica6/mathematica'
```
Then on, invoking Mathematica 6 is as simple as "mathematica6".

---

