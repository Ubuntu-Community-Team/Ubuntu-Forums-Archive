---
title: "installing latest version  amsn"
date: 2007-01-26
forum: General Help
---

### Post by PetePete on 2007-01-26
i'm trying to upgrade to the latest version of amsn, but the repositories only are upto 0.95 and 0.96 is avaliable....

I've tried the 'generic installer' but that just stops , i've tried the compiling from source but that comes up with an error about tcl ... 

is there a .deb of the latest version avliable anywhere?

---

### Post by pay on 2007-01-26
You also need tcl. Try ```
sudo apt-get build-dep amsn
```or if that doesn't work the source for tcl is here [http://www.tcl.tk/software/tcltk/downloadnow85.html](http://www.tcl.tk/software/tcltk/downloadnow85.html)

---

### Post by PetePete on 2007-01-26
legend :)
compiles nicely now

thx

---

### Post by lamego on 2007-01-26
You you can install from a .deb:
[http://www.getdeb.net/app.php?name=amsn](http://www.getdeb.net/app.php?name=amsn)

---

### Post by dreamwarrior on 2007-02-25
> **lamego said:**
> You you can install from a .deb:
[http://www.getdeb.net/app.php?name=amsn](http://www.getdeb.net/app.php?name=amsn)

hi....i did this,and it appears to be installed,but when i try to run it, it simply doesnt run...it appears in the applications ,but wont work....Im new using ubuntu...can anyone explain to me how to do it step by step in any way,even withthe commands...but please,understand  im really new at this,thats why i asked to be step by step..thanks for your help....dreamwarrior

---

