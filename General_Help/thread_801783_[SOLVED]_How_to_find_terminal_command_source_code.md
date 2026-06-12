---
title: "[SOLVED] How to find terminal command source code?"
date: 2008-05-20
forum: General Help
---

### Post by jays455 on 2008-05-20
Hello, I am in the process of learning the C language, so I wanted to practice it trying to write the built-in programs in Linux. I was trying to re-write 'man' and 'cat'. Can anyone tell me how I can view the source code for these 2 programs? I am using Ubuntu 7.10.

Thank you for your help.

---

### Post by tamoneya on 2008-05-20
its should all be in bash.
[http://tiswww.case.edu/php/chet/bash/bashtop.html](http://tiswww.case.edu/php/chet/bash/bashtop.html)

---

### Post by jays455 on 2008-05-20
I'm sorry, I'm fairly new to ubuntu. I went to the bash wesbite but I am not sure what to do from there. Can you please provide some more guidance? Thank you again.

---

### Post by amingv on 2008-05-20
You can always get the source of any [open source] program in their homepage (for example search "gnu bash" and you'll find this: [http://www.gnu.org/software/bash/](http://www.gnu.org/software/bash/)).

Alternatively, you can download source from the repos:
```
apt-get source bash
```

Be aware, however, that source from the repos may be modified to better suit Ubuntu.

---

### Post by sdennie on 2008-05-20
You should be able to get the source code for any app on your system with:

```

sudo apt-get source name-of-package

```

Though, in the case of "man", I believe it uses "nroff" or "troff" or some sort of "roff" to do the output formatting so, it may be easier to write a shell script to emulate it.  As for cat, that should be pretty straightforward...

---

### Post by wdaniels on 2008-05-20
I believe cat is in the coreutils package, and man is in man-db. Probably coreutils is the kind of stuff you're looking for.

---

### Post by tamoneya on 2008-05-20
this was linked about half way down: [ftp://ftp.gnu.org/gnu/bash/bash-3.2.tar.gz](ftp://ftp.gnu.org/gnu/bash/bash-3.2.tar.gz).

If you are so new to ubuntu that you cant read through that short bash page you are goin to have a lot of trouble sorting through the bash source code.

---

### Post by amingv on 2008-05-20
@OP

You might be interested in trying to implement a "lite" version yourself and then look at the source (for example cat shouldn't be too hard once you learn file management), but that's just my unsolicited opinion.

---

### Post by 3rdalbum on 2008-05-20
Answered better above.

---

### Post by jays455 on 2008-05-21
Thank you everyone for your responses. Since I'm just in the learning process, I'm only trying to do some basic things. For example: the cat program that I am doing isn't really the full blown one that is on the OS. I'm just implementing a few arguments and building from there. 
Anyway, thanks again for your help.

---

