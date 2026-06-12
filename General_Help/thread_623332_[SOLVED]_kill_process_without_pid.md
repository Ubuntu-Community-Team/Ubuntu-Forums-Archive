---
title: "[SOLVED] kill process without pid"
date: 2007-11-25
forum: General Help
---

### Post by oneadvent on 2007-11-25
I'm sorry, I know it is here somewhere....

Lets just make it easy to find for others. (I couldn't find it.)

What is the best way to kill a program if you do not know the pid.

This is for use in a shell script.

Thanks

---

### Post by sirdilznik on 2007-11-25
```
killall <name of process>
```
if that fails 
```
killall -9 <name of process>
```
note that this close ALL instances of that process so if you use this to close xterm and you have 5 xterms open, it will close all of them.

---

