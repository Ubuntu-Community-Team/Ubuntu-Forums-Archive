---
title: "Help installing lxdream on ubuntu 7.10"
date: 2007-11-27
forum: General Help
---

### Post by UK-Wobbie on 2007-11-27
Do any one know how to install Linuxdream the Dreamcast Emulator for Linux on Ubuntu? I am having no luck on it :(
I need step by step help :lolflag:
Thanks :)

---

### Post by UK-Wobbie on 2007-11-29
Any one? :(

---

### Post by lunarcloud on 2007-12-21
You have to install automake, autoconf, build-essential, esound and libesd0-dev plus you'll have to link to the real libGL.so like so

```

sudo apt-get install automake autoconf build-essential esound libesd0-dev
sudo ln -s /usr/lib/libGL.so* /usr/lib/libGL.so
sudo sh autogen.sh
sudo make install

```

Or something... it'l been a while.

---

### Post by PinkFloyd102489 on 2007-12-21
There's a Dreamcast emulator in the repositories, fyi.

---

