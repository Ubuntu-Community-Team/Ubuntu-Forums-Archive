---
title: "Something is seriously wrong with java"
date: 2013-04-26
forum: General Help
---

### Post by rhelmot on 2013-04-26
Ubuntu 12.04, running "java" from the terminal nets me this:

```
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 460: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!
```

Yeah.

The only thing I can think of that might help is that I installed openjdk 7 with apt-get, but the first time I tried that dpkg hit a segfault and I had to finish the install with sudo dpkg --configure -a like it tells you to.

---

### Post by r.stiltskin on 2013-04-26
Try

sudo apt-get check

sudo ldconfig  -v

---

### Post by Mopar1973Man on 2013-04-26
There is a way to install Oracle Java.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by rhelmot on 2013-04-27
> **Mopar1973Man said:**
> There is a way to install Oracle Java.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
That did it :D

Thank you, everybody. This is my first time using these forums for assistance and it's nice to know that the people around here know their stuff!

---

