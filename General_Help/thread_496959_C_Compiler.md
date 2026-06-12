---
title: "C Compiler"
date: 2007-07-09
forum: General Help
---

### Post by rkrizan on 2007-07-09
I'm getting this error when trying to configure Pidgin. Or any other source packages from that matter: 

checking for C compiler default output file name... configure: error: C compiler cannot create executables

Anyone know how to fix this?

---

### Post by scorpion_gr on 2007-07-09
I'm having the same error with compilation... I don't remember what I was trying to compile

---

### Post by rkrizan on 2007-07-09
ld: crtbegin.o: No such file: No such file or directory

That probably has something to do with it.

---

### Post by rkrizan on 2007-07-09
I keep getting the same responses on efnet and freenode, "sudo apt-get install build-essential" - However, I've already installed it. Any suggestions?

---

### Post by joshthewhistler on 2007-07-12
I cannot get this to work either. I am trying to install alsa and when I run ./configure it spews out an error:

configure: error: C compiler cannot create executables

Any help?

---

### Post by Noma4i on 2007-07-13
> **joshthewhistler said:**
> I cannot get this to work either. I am trying to install alsa and when I run ./configure it spews out an error:

configure: error: C compiler cannot create executables

Any help?

same problem. Looks like Ubuntu Live CD has this bug.

Newly installed Ubuntu can't compile over 90% of programm src

---

### Post by Noma4i on 2007-07-13
sudo apt-get install build-essential

found this on forum. All works)

---

