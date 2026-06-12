---
title: "Compiling from source"
date: 2006-11-28
forum: General Help
---

### Post by Jammy_Stuff on 2006-11-28
I'm currently trying to install Crossover Office by compiling it from the source code (I'm a student so can't really afford to pay for the compiled form) but have noticed the lack of a makefile or anything like that. What do I need to do?

---

### Post by tribaal on 2006-11-28
Sometimes the makefile is generate by a "configure" script (not sure about crossover office).

Try to issue a "./configure" command in the source's root directory before the "make" and "make install" commands.

Hope this helps... Maybe Crossover has a specific compilation method, but i'm not familiar with it unfortunately.

- trib'

---

### Post by Jammy_Stuff on 2006-11-28
The thing is, the source is actually 4 separate programs which can all be installed. However, do they need to be installed in a special way or anything?

---

### Post by taurus on 2006-11-28
Is there a README or INSTALL that you can look at?  Most of the time, either one of those files will tell you what you need to compile it and how to install it...

---

### Post by PotOfVB on 2006-11-28
hi jammy,

open up terminal (_apps.>accessories>terminal_)
go to root directory where of extracted Crossover office e.g _cd /home/Your Username/crossover_
type _ls_ into terminal
what files are there?
if _configure_ is there, type the following one at a time and in order:
type_ ./configure_
type _sudo make_
type _sudo make install_

also you may additional packages to compile
e.g c++ compiler development packages etc

---

### Post by LLRNR on 2006-11-28
Not sure about Crossover Office, but maybe you'll find these useful in a certain way:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

and

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

HTH,

LLRNR

---

