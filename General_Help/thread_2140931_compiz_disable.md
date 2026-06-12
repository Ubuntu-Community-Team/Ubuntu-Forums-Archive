---
title: "compiz disable"
date: 2013-05-01
forum: General Help
---

### Post by Georgescu1 on 2013-05-01
I am running ubuntu 12.04
Each time i disable my compiz (for more power)
```
metacity --replace
```
On the left side of my screen it will appear a black square that will be over any application/desktop(has like a topmost function)
If i re enable compiz
```
compiz --replace
```
The problem dissapears

Any sollution for the problem? Thanks in advanced

---

### Post by dino99 on 2013-05-01
check that the graphic driver is well installed and activated (jockey-gtk/additional drivers)

to reset compiz: ```
compiz --replace ccp & 
```

---

### Post by Georgescu1 on 2013-05-01
The answer did not really help me
After some time of playing around with my frustration found out that the problem is in metacity and it is caused by the cairo dock(the background is not transparent it is black)

I don't want to open a new thread so.... how do i make a bash script or something simmilar(shortcut maybe) that can toggle between starting and stopiing cairo dock?

---

