---
title: "C Compiler problem"
date: 2006-07-17
forum: General Help
---

### Post by Pyro MX on 2006-07-17
I've been trying to install the Freetype plugin for GIMP, but when I do ./configure, here's what shows up:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I had to install the GCC package (with Adept, I use Kubuntu 6.06) because the thing wasnt finding GCC. What can I do to make it work?:-k

---

### Post by Pyro MX on 2006-07-17
I installed  GCC and all the stuff the ./configure looked for, installed dev files for the gimp, and it worked. Yay! It's odd that 6.06 didn't come with GCC - I think it was included in 5.10.

---

### Post by taurus on 2006-07-17
Sorry but none of the Ubuntu releases have ever installed gcc as default even though it's on the CD!  You have to install it by hand after with

```

sudo apt-get install build-essential

```

---

### Post by Pyro MX on 2006-07-17
Ah, my mistake then! Got the build-essential, worked great! Thanks!

---

### Post by Eggbanjo on 2006-09-02
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential

thats what i get tho... help!

---

### Post by ifokkema on 2006-09-02
build-essential is in main... Hmmm...
What does your /etc/apt/sources.list look like?

---

### Post by taurus on 2006-09-02
Actually, build-essential is even on the CD!!!

```

sudo aptitude update
sudo aptitude install build-essential

```

---

