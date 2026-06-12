---
title: "Missing File - What is it and where can I get it?"
date: 2022-01-06
forum: General Help
---

### Post by rsteinmetz70112 on 2022-01-06
I had a problem with one of my Ubuntu 18.04 x86 computer. I ran a routine update and got an error message about a missing file.
```
 /usr/lib/i386-linux-gnu/libhybris-egl/ld.so.conf
```
What is it? Do I need it? Where can I get it?

---

### Post by slooksterpsv on 2022-01-07
It looks like its a file for ES GL. You don't necessarily need it as something could have superseded it. If things are running fine, don't worry about it.

Otherwise, you may need to attempt to install libhybris-egl from apt in the terminal (if available) - either that or compiling it yourself.

---

### Post by rsteinmetz70112 on 2022-01-07
Things seem to be working so far. I'll keep an eye out. I removed a bunch of old configuration files whihc also seems to have removed some random files here and there. I'm not sure what was removed It did break mysql, whihc I've repaired and some other stuff.

---

