---
title: "[SOLVED] extremely basic question about cd command"
date: 2008-01-29
forum: General Help
---

### Post by einherier on 2008-01-29
like...why cant i get into this folder?


pra3torian@pra3torian:/$ ls
bin    dev       GPL.txt  initrd.img  lib64       mnt   root  sys  var
boot   etc       home     lib         lost+found  opt   sbin  tmp  vmlinuz
cdrom  EULA.txt  initrd   lib32       media       proc  srv   usr
pra3torian@pra3torian:/$ cd ect
bash: cd: ect: No such file or directory
pra3torian@pra3torian:/$ cd ect
bash: cd: ect: No such file or directory
pra3torian@pra3torian:/$ cd /ect
bash: cd: /ect: No such file or directory
pra3torian@pra3torian:/$ cd ./ect
bash: cd: ./ect: No such file or directory
pra3torian@pra3torian:/$ #**** YOU!

---

### Post by aysiu on 2008-01-29
Try ```
cd etc
``` instead of ```
cd ect
```

---

### Post by bodhi.zazen on 2008-01-29
tab completion helps reduce typos as well.

Start typing a location :

e

hit the tab :

e<tab>

if there is only one option, tab will complete it. Otherwise hit tab twice to list options.

Tab completion works for files, directories, and commands

---

### Post by ~LoKe on 2008-01-29
Be careful when using tab completion, though.  You might end up in the wrong directory and do something quite awful. ;)

---

### Post by einherier on 2008-01-29
> **aysiu said:**
> Try ```
cd etc
``` instead of ```
cd ect
``` 

Good lord......  This is exactly why i gave up C

thanks....god its always embarrassing when you make such a damned elementary mistake

---

### Post by einherier on 2008-01-29
> **bodhi.zazen said:**
> tab completion helps reduce typos as well.

Start typing a location :

e

hit the tab :

e<tab>

if there is only one option, tab will complete it. Otherwise hit tab twice to list options.

Tab completion works for files, directories, and commands


That's a good tip.  Thanks also to loke.

[Solved]

---

