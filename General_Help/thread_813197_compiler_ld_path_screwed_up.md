---
title: "compiler ld path screwed up"
date: 2008-05-30
forum: General Help
---

### Post by dracayr on 2008-05-30
hi,

I'm trying to build a lfs (linux from scratch). However, gcc sometimes gives me this error (note that this is not the gcc of the host system, but the gcc that I compiled myself while building the lfs):

```
unrecognized option '--hash-style=both'
ld exit 1
```

I believe this is the reason:

```
lfs@dracayr-lab:/home/dracayr/src/dejagnu-1.4.4$ gcc -print-prog-name=ld
/home/dracayr/tools/bin/../lib/gcc/i686-pc-linux-gnu/4.1.2/../../../../i686-pc-linux-gnu/bin/ld
```

I think that path should be either /tools/bin/ld or /home/dracayr/tools/bin/ld (which is the same because /tools is a symlink. /home/dracayr is where my second partition is mounted).

My question is, how do I set the path?

I use Ubuntu hardy, the book is version 6.3

thanks in advance,
dracayr

---

