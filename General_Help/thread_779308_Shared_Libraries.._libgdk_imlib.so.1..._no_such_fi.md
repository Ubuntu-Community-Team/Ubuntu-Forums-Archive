---
title: "Shared Libraries.. libgdk_imlib.so.1... no such file"
date: 2008-05-02
forum: General Help
---

### Post by AlarmingSword on 2008-05-02
```
lolwut@lolwut:~$ razorback 
razorback: error while loading shared libraries: libgdk_imlib.so.1: cannot open shared object file: No such file or directory
lolwut@lolwut:~$ 
```

While running razorback, I get the above- i've installed a lot of things, and have been searching for ages :( 

Any ideas?

Edit: I'm using Hardy Heron, if that helps.

---

### Post by Grishka on 2008-05-02
did you install gdk-imlib11 library?

---

### Post by AlarmingSword on 2008-05-02
Yes, and I checked the dependencies by hand.

I installed razorback from the repositories.

---

### Post by Grishka on 2008-05-02
> **AlarmingSword said:**
> Yes, and I checked the dependencies by hand.

I installed razorback from the repositories.

from what repositories? check for libgdk_imlib.so.x.x.x library in /usr/lib/ folder. if it's there, maybe you just need to make a symbolic link "libgdk_imlib.so.1" to it.

---

### Post by AlarmingSword on 2008-05-02
I apologize, I figured it out.

A little searching and I found it.

a simple 

```
 
sudo apt-get install gdk-imlib1

sudo apt-get install libdb1-compat


```

Fixed it.

Again, I apologize. 

(Not to get too off topic, but all the log parsers apart from razorback aren't compatible- do you guys know of any that work with 2.7.0, or management utilities for snort? Thanks!)

---

### Post by sherbieny on 2010-12-12
when I wrote apt-get install gdk-imlib1 this what I got

root@ubuntu:~# apt-get install gdk-imlib11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdk-imlib11

---

### Post by sherbieny on 2010-12-12
when I wrote apt-get install gdk-imlib1 this what I got

root@ubuntu:~# apt-get install gdk-imlib11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdk-imlib11

---

