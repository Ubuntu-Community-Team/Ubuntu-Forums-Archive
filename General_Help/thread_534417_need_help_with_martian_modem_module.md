---
title: "need help with martian modem module"
date: 2007-08-25
forum: General Help
---

### Post by mykrob on 2007-08-25
Hey-

having a pretty simple problem compiling the martian modem driver.. Here's what i get from running "make all"

```

sherwin@ubuntu:~/Downloads/Modem Tools/martian/martian$ make all
make -C kmodule/ modules
make[1]: Entering directory `/home/sherwin/Downloads/Modem Tools/martian/martian/kmodule'
make -C /lib/modules/2.6.20-16-386/build M="/home/sherwin/Downloads/Modem Tools/martian/martian/kmodule"  modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.20-16-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/sherwin/Downloads/Modem Tools/martian/martian/kmodule'
make: *** [all] Error 2


```

seems like a sym link may fix it, but i would like confimartion.

thanks,
-myk

---

### Post by acacs on 2007-08-26
It seems that you need to install the linux-source package. Run the following at the command line, as normal user:

```
sudo aptitude update && sudo aptitude install linux-source
```

Then repeat what you did before.

---

### Post by mykrob on 2007-08-27
thanks, i ill try that

---

### Post by mikeescott on 2007-08-28
I am having a similar problem after upgrading to Feisty. I am now unable to dial onto the internet from Ubuntu. Had to get back into XP to get here. Can I download the source in Windows and save to install in Ubuntu later?

> **acacs said:**
> It seems that you need to install the linux-source package. Run the following at the command line, as normal user:

```
sudo aptitude update && sudo aptitude install linux-source
```

Then repeat what you did before.

---

