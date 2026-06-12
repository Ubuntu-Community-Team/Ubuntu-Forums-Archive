---
title: "Cannot install gmake on Ubuntu 20"
date: 2021-03-10
forum: General Help
---

### Post by chuchi on 2021-03-10
Hello everyone!

Is gmake gone on Ubuntu 20? How can I install gmake? I have some old scripts that execute 'gmake'.

Thanks a lot!

---

### Post by Impavidus on 2021-03-10
On my Xubuntu 20.10, /usr/bin/gmake is a symbolic link to /usr/bin/make. It's provided by the make package (along with the make command it points to).

---

### Post by TheFu on 2021-03-10
On my 20.04 system, the package name is 'make'.

```
$ dpkg -S /usr/bin/make
make: /usr/bin/make

$ make --version
GNU Make 4.2.1
Built for x86_64-pc-linux-gnu
```

---

### Post by chuchi on 2021-03-10
Hello guys thanks for your answers!

I can execute 'make' without problems. My original problem is that I cannot execute 'gmake', and I have some scripts that execute 'gmake'. 

But I just learned that Ubuntu 20 does not support gmake anymore, only make. So I have to change my scripts to replace 'gmake' with 'make'.

Thanks a lot!

---

### Post by TheFu on 2021-03-10
> **chuchi said:**
> Hello guys thanks for your answers!

I can execute 'make' without problems. My original problem is that I cannot execute 'gmake', and I have some scripts that execute 'gmake'. 

But I just learned that Ubuntu 20 does not support gmake anymore, only make. So I have to change my scripts to replace 'gmake' with 'make'.

Thanks a lot!

Well, not really. You could make a symbolic link or hard link from gmake to make.  Trivial.  Both of these capabilities have been part of Unix file systems for 40+ yrs - probably longer.  The **ln** command will let you make both.
[LIST]
[*][https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link)
[*][https://en.wikipedia.org/wiki/Hard_link](https://en.wikipedia.org/wiki/Hard_link)
[/LIST]

The correct answer is for your scripts to do what build scripts have done for 30 yrs and have it determine which version of make is on the system, then use that.  autoconf does that as to lots and lots of other build scripts.

BTW, I'm a gmake bigot. We automated all our build scripts/makefiles to use gmake everywhere I worked that did C/C++ programming. We even used gmake on Windows platforms to build our software. It was much more repeatable that way.

---

### Post by Impavidus on 2021-03-10
gmake is the GNU version of make and is the default on Ubuntu. But the executable is called make, not gmake. The simple solution is what apparently is the default on 20.10 (but not on 20.04): just create a symlink called gmake and have it point to make.

---

