---
title: "cannot open crti.o: No such file or directory"
date: 2008-01-18
forum: General Help
---

### Post by yoda_143 on 2008-01-18
First of all I am a linux beginner, so be patient with me.
Yesterday I installed Ubuntu 7.10 on my Compaq TC1000 tablet PC.
Everything went fine. The first thing after installing was trying to enable the pen input by [this guide]("http://www.handhelds.org/hypermail/tc1000-linux/att-0425/fpi2002-pen.txt").
It fails in the last step, command: ```
gcc -shared -Wl,-soname,tc1k_drv.so -o tc1k_drv.so tc1k_drv.o -lc
```
It returns the error message: ```
cannot open crti.o: No such file or directory 
```
I manually searched for the apparently missing, but it could not be found. 
What do I have to install to fix this situation?

---

### Post by jeffus_il on 2008-01-18
This thread will help you.

[http://ubuntuforums.org/showthread.php?t=202136](http://ubuntuforums.org/showthread.php?t=202136)

---

### Post by yoda_143 on 2008-01-18
Thanks for your reply, but this did not fix my problem. It's for an old method of enabling the pen input as far as I can tell. The error message in the thread you linked was also different from mine.
Again: It's looking for a crti.o in usr/bin/ld which it cannot find. How do I get this file?

---

### Post by jeffus_il on 2008-01-18
You need to install the package libc6-dev.

---

### Post by yoda_143 on 2008-01-18
Thanks, now it worked without error.
The pen however is still not working after reboot. I followed the guide linked above to the letter, so I have no idea why it doesn't work.

---

