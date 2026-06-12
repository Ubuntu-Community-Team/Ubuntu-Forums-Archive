---
title: "Silly question about tar"
date: 2008-07-08
forum: General Help
---

### Post by kdorf on 2008-07-08
Something I've always wondered (and have never been sure of) - why is it that people use two -v flags when they use tar? It's not everywhere -- some only use one -v flag, but you definitely see it in the manual (man tar). Does it make the output more verbose?

Sorry if that sounds stupid. =P

---

### Post by VMC on 2008-07-08
Maybe they are using two different volumes in the tar message. Also, of course, the "V" is for verbose.

---

### Post by womblet on 2008-07-08
Hi.
I can't figure out how to post a new message so I thought I would ask here.
I think it is related to tar too. I downloaded a program with the name anylogic-advanced-6.2.2.linux.i586.tgz.bin

Is a .tgz.bin suffix similar to a tar?

I tried searching and couldn't find anything that explained how to install this... I'm sure I'm misunderstanding something.

Thanks for your help.

---

### Post by justleen on 2008-07-08
i've never seen the use of two v's, personally..
you could have -vV, when creating an archive ( v for verbose, V for LABEL)

if you add 1 extra v, you get "more verbose" but the working is exaclty the same

@womblet:  that extension is wrong, it should be .bin.tgz OR it is a binary file..
try to extract with```

tar -zxvf  anylogic-advanced-6.2.2.linux.i586.tgz.bin 
```
or try to execute with
```

chmod +x anylogic-advanced-6.2.2.linux.i586.tgz.bin
./anylogic-advanced-6.2.2.linux.i586.tgz.bin

```

---

### Post by womblet on 2008-07-08
Thanks, the code:

> 
chmod +x anylogic-advanced-6.2.2.linux.i586.tgz.bin
./anylogic-advanced-6.2.2.linux.i586.tgz.bin

worked fine

---

