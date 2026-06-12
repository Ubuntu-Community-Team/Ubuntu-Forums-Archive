---
title: "Trying to understand 'time' output"
date: 2007-05-28
forum: General Help
---

### Post by yinglcs2 on 2007-05-28
hi, 

I use time to time how much my script take, and here is the result
$ time myscript
real    0m13.786s
user    0m0.376s
sys     0m0.128s

My question si why "user" + "sys" != "real"?

---

### Post by fanatik on 2007-05-29
there may also be iowait in there too, ie the time waiting for I/O, time doesn't show that. it depends what your script does. typing: **vmstat 1** will show you.

---

