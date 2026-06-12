---
title: "&quot;C compiler cannot create executables&quot; error"
date: 2007-02-23
forum: General Help
---

### Post by funkadelic on 2007-02-23
I often get the error message: "C compiler cannot create executables" when I try to compile software - what does this mean and how can I fix it? (i.e. WHY can't the compiler create executables if I run it with sudo?)

---

### Post by maxamillion on 2007-02-23
can you copy and paste an example error ... preferably the entire error and maybe some sample code if applicable

---

### Post by funkadelic on 2007-02-23
I am trying t compile an XMMS plugin to play .shn files...

> bozo@bozo-box:~/Desktop/xmms-shn-2.4.0$ sudo ./configure
Password:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
bozo@bozo-box:~/Desktop/xmms-shn-2.4.0$ 


---

### Post by nickoli_02 on 2007-02-23
How about we see what's inside config.log? Supposedly there's more details about the error in there ;)

---

### Post by yabbadabbadont on 2007-02-23
Have you actually *installed* a C compiler yet?  Dev tools are not included in the default installs.  "sudo apt-get install build-essential" will get you some of what you need.  "xorg-dev" will get you a lot more.

EDIT: Actually, it looks like you at least have gcc installed from that config output.:-k

---

### Post by sardion on 2007-02-23
The issue is in the sudo

You should not run configure with sudo

I won't go into details about how sudo works, but when you compile stuff do:

./configure
make
sudo make install

only sudo the end

---

### Post by nickoli_02 on 2007-02-23
> **sardion said:**
> The issue is in the sudo

You should not run configure with sudo

I won't go into details about how sudo works, but when you compile stuff do:

./configure
make
sudo make install

only sudo the end

Instead of running sudo make install, a better alternative is to install checkinstall from the repos. Checkinstall allows you to remove the package later with synaptics if you wish... I don't know all the details as to why checkinstall is superior but it seems to be the preferred choice

```
sudo aptitude install checkinstall
```

Now instead of sudo make install,

```
sudo checkinstall
```

---

### Post by Perfect Storm on 2007-02-23
Checkinstall does not always work, but worth trying first, if it doesn't just use sudo make install.

---

### Post by yabbadabbadont on 2007-02-23
> **Artificial Intelligence said:**
> Checkinstall does not always work, but worth trying first, if it doesn't just use sudo make install.

It doesn't work with tovid for some reason.  It gets the program files correct, but it completely misses the man pages.  I tried it both with fstrans enabled and disabled, but it didn't work either way.  The checkinstall homepage said something about trouble when certain utilities on the system are statically linked instead of dynamically.  :-?

---

### Post by nickoli_02 on 2007-02-23
> **yabbadabbadont said:**
> It doesn't work with tovid for some reason.  It gets the program files correct, but it completely misses the man pages.  I tried it both with fstrans enabled and disabled, but it didn't work either way.  The checkinstall homepage said something about trouble when certain utilities on the system are statically linked instead of dynamically.  :-?

hmm I guess that's good to keep in mind. Thanks for the tip :popcorn:

---

