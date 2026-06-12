---
title: "Why does this error appear on my machine?"
date: 2013-06-13
forum: General Help
---

### Post by jon80 on 2013-06-13
Why does this error appear on my machine?

jonathan@ubuntu:~$ gcc
gcc: fatal error: no input files
compilation terminated.
jonathan@ubuntu:~$ gcc print.c
gcc: error: print.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.
jonathan@ubuntu:~$ touch print.c
jonathan@ubuntu:~$ gcc print.c
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
jonathan@ubuntu:~$

---

### Post by CaptainMark on 2013-06-13
1. gcc requires you to pass it a file
2. the file print.c does not exist in the current directory so you can't run pass it to gcc
3. touch creates a completely empty file so gcc fails to compile it because it has no information in it

---

### Post by Frogs Hair on 2013-06-13
This is dated , but may be of help.  [http://ubuntuforums.org/archive/index.php/t-1030742.html](http://ubuntuforums.org/archive/index.php/t-1030742.html)

---

