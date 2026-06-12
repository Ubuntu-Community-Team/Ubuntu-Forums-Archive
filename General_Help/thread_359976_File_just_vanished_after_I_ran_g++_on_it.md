---
title: "File just vanished after I ran g++ on it"
date: 2007-02-12
forum: General Help
---

### Post by mercurysquad on 2007-02-12
:confused: Look at this terminal session :
```

Feisty> **vim funcs_1_2b.c**    *followed by some editing for an hour*
Feisty> **g++ funcs_1_2b.c -o funcs_1_2b.c -Wall**
/tmp/ccKMHTM3.o: In function `main':
funcs_1_2b.c:(.text+0xd3): undefined reference to `pthread_create'
funcs_1_2b.c:(.text+0x124): undefined reference to `pthread_create'
funcs_1_2b.c:(.text+0x15f): undefined reference to `pthread_join'
funcs_1_2b.c:(.text+0x197): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
Feisty> **g++ funcs_1_2b.c -o funcs_1_2b.c -Wall -pthread**
g++: funcs_1_2b.c: No such file or directory
g++: no input files
Feisty> **ls**
a1-1.pdf  hw1-1.2a.c  hw1a

```
There goes my 1 hour worth of coding, it's 11pm and I wanted to get some sleep. :mad: 
I AM SUCH AN IDIOT.
Anyway, does anyone know a way to recover the file? Restarting vim doesn't find any swap file to recover from. :(
And I think the file specified after -o should not be deleted/overwritten unless the build was sucessful. And especially if input and output files are the same.

---

