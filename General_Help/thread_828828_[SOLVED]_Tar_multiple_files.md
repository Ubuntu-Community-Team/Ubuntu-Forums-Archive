---
title: "[SOLVED] Tar multiple files"
date: 2008-06-14
forum: General Help
---

### Post by geo909 on 2008-06-14
Hello everybody

I am in a directory and want to tar all th files..
I do 
```
tar -cvf *
```
Shouldn't this work?

That's the output, no file seems to be created:
```

jorge@linux-kupy:~/Desktop/&#928;&#961;&#959;&#963;&#969;&#961;&#953;&#957;&#940;/14June08> l
total 59K
-rwxrwxrwx 1 root root  30K 2008-06-14 13:15 ints.c
-rwxrwxrwx 1 root root   58 2008-06-14 12:41 ints.h
-rwxrwxrwx 1 root root  197 2008-06-14 12:43 makefile
-rwxrwxrwx 1 root root  182 2008-06-14 12:43 strings.c
-rwxrwxrwx 1 root root  133 2008-06-14 12:38 strings.h
-rwxrwxrwx 1 root root 9.1K 2008-06-14 12:44 test
-rwxrwxrwx 1 root root  177 2008-06-14 12:41 test.c
-rwxrwxrwx 1 root root 9.1K 2008-06-14 12:23 today
jorge@linux-kupy:~/Desktop/&#928;&#961;&#959;&#963;&#969;&#961;&#953;&#957;&#940;/14June08> tar -cvf *
ints.h
makefile
strings.c
strings.h
test
test.c
today
jorge@linux-kupy:~/Desktop/&#928;&#961;&#959;&#963;&#969;&#961;&#953;&#957;&#940;/14June08> l
total 59K
-rwxrwxrwx 1 root root  30K 2008-06-14 13:16 ints.c
-rwxrwxrwx 1 root root   58 2008-06-14 12:41 ints.h
-rwxrwxrwx 1 root root  197 2008-06-14 12:43 makefile
-rwxrwxrwx 1 root root  182 2008-06-14 12:43 strings.c
-rwxrwxrwx 1 root root  133 2008-06-14 12:38 strings.h
-rwxrwxrwx 1 root root 9.1K 2008-06-14 12:44 test
-rwxrwxrwx 1 root root  177 2008-06-14 12:41 test.c
-rwxrwxrwx 1 root root 9.1K 2008-06-14 12:23 today
jorge@linux-kupy:~/Desktop/&#928;&#961;&#959;&#963;&#969;&#961;&#953;&#957;&#940;/14June08>


```

---

### Post by geo909 on 2008-06-14
Sorry, I was using wrong syntax!
I found it now..

---

### Post by kanna1620 on 2009-09-02
> **geo909 said:**
> Sorry, I was using wrong syntax!
I found it now..

Could you please post the correct syntax :)

---

