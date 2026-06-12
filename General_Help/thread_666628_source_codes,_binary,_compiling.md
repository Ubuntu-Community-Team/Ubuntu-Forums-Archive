---
title: "source codes, binary, compiling???"
date: 2008-01-13
forum: General Help
---

### Post by dzuari on 2008-01-13
im new to linux, i just installed ubuntu and iv been trying to get some programs to run that i  downloaded but i have to use codes of some sort, will someone plz enlighten me on wat this is and how to do it

---

### Post by Craigus on 2008-01-13
No, because you haven't provided any useful information.

What programs are you trying to install ?

Have you looked to see if they are available in synaptic ?  System-Administration-Synaptic Package Manager.

If so, you will not have to compile anything.

---

### Post by Borbus on 2008-01-13
Have you tried searching the Ubuntu repositories for binaries before trying to compile. If it's a fairly well known program, chances are it is in the repos. Go to Add/Remove... and search for it there.

If it isn't in the repos, then first you could try to look for a deb package, which is a binary made for Debian/Ubuntu (well, apt, technically).

If you really have to compile then always read the readme file, it should tell you how to. You need to make sure you have any dependancies, again the readme should tell you this information. A common way to compile a program is:
```

./configure
make
sudo make install

```
When you have already extracted the source files and changed to the directory where the Makefile is.

---

### Post by dzuari on 2008-01-13
i need to kno wat all this is because iv never done any of this before, im use to click and installing

---

### Post by Craigus on 2008-01-13
And you still haven't provided any information that will allow people to help you.

You *can* click and install in ubuntu, if the programs you want are in the repositories, or if you can download a .deb package.

What are you trying to install ?

---

### Post by Steveway on 2008-01-13
Open up Synaptic from your menu.
It will ask for your password.
Then search for the software that you want to install.
Mark it for installation and if you marked everything you want then click apply.
It'll download and install everything for you.
You should try to install from source later if you got more knowledge and experience.

---

### Post by dzuari on 2008-01-13
im trying to install hydra_5.3-src-1_i386.deb, but dont kno how

---

### Post by dzuari on 2008-01-13
alright i figured out how to install packages with the synaptic but how do i find them now so i can use them

---

### Post by Craigus on 2008-01-13
I think hydra has to be run from a terminal. Applications-Accessories-Terminal.

[http://www.linux.com/articles/47455]("http://www.linux.com/articles/47455")

---

