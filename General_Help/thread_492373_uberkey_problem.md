---
title: "uberkey problem"
date: 2007-07-04
forum: General Help
---

### Post by joriad on 2007-07-04
I have been trying to install uberkey and am comming up with these errors 

```
x@x:~$ make
gcc -s -O3 -o uberkey uberkey.c
uberkey.c:8:18: error: time.h: No such file or directory
uberkey.c:9:20: error: unistd.h: No such file or directory
uberkey.c:10:23: error: sys/types.h: No such file or directory
uberkey.c:11:23: error: sys/param.h: No such file or directory
uberkey.c:19:20: error: sys/io.h: No such file or directory
uberkey.c: In function &#8216;main&#8217;:
uberkey.c:30: error: storage size of &#8216;test&#8217; isn&#8217;t known
uberkey.c:34: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
uberkey.c:56: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
make: *** [all] Error 1
x@x:~$
``` 

I have the uberkey.c, uberkey.8 and the makefile but still I have no luck with this.
Can any one help?

Thanks.

---

### Post by McNils on 2007-07-04
Essential header files seems to be missing. Try to install libc6-dev. ```
sudo apt-get install libc6-dev
```

---

### Post by joriad on 2007-07-04
Thanks, that seems to have worked.

---

### Post by joriad on 2007-07-04
I have uberkey installed. But now, I seem to have a problem with keyboard entries. 
Every time I try to enter text into a different field or use the mouse and then return to
the keyboard the first key entry does not show up in those fields but is recorded in the keylog file.

Has anyone else used Uberkey and come across this problem?

---

### Post by Jimerson on 2008-01-24
I have a very similar problem. The first letter doesn't appear and if I don't type slow ,other letter tend to not appear.

---

