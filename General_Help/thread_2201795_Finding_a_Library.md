---
title: "Finding a Library"
date: 2014-01-25
forum: General Help
---

### Post by sundaykid95 on 2014-01-25
I am trying to compile qjoypad but when I try to uses the following command "./config" when in the proper location, terminal tells me that I need libxtst. Now when I try to execute the command "Sudo apt-get install libxtst" it runs, but it cannot find libxtst. Any help?

---

### Post by claracc on 2014-01-26
Please, read this thread: [http://ubuntuforums.org/showthread.php?t=1518647](http://ubuntuforums.org/showthread.php?t=1518647), specially, post number 4, where there is a workaround propossed:

```
qjoypad-4.1.0/src$ ./config
Error: you will need libxtst to compile this program

sudo aptitude install libxtst-dev

then head back to
./configure
make
sudo make install 
```

The thread is old, but the problem seems to be the same.

---

### Post by deadflowr on 2014-01-26
Search the software center.

---

### Post by kostkon on 2014-01-26
[AntiMicro]("http://www.webupd8.org/2013/09/map-keyboardmouse-input-to-your-gamepad.html") is probably an better choice nowadays.

---

### Post by oldos2er on 2014-01-26
> **sundaykid95 said:**
> I am trying to compile qjoypad but when I try to uses the following command "./config" when in the proper location, terminal tells me that I need libxtst. Now when I try to execute the command "Sudo apt-get install libxtst" it runs, but it cannot find libxtst. Any help?

You need the exact package name: ```
apt-cache search libxtst
``` or even better since you know you need the dev library: ```
apt-cache search libxtst dev
``` Hope that helps.

---

### Post by sundaykid95 on 2014-01-26
> **kostkon said:**
> [AntiMicro]("http://www.webupd8.org/2013/09/map-keyboardmouse-input-to-your-gamepad.html") is probably an better choice nowadays.
Thank you, but now I run across the problem of not having libsdl2-2.0-0(>=2.0.0). I'm relatively new to Ubuntu and I am using 12.04, probably should have said that before.

---

### Post by sundaykid95 on 2014-01-26
For those who are saying things for qjoypad, it fixed that issue, but now I need to update to at least Qt 4.2, which I need help with. I'm hopeless XD

---

### Post by sundaykid95 on 2014-01-26
Never mind Kostkon, I just had to select a different package. I've got it now.

---

