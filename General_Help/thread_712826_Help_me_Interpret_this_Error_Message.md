---
title: "Help me Interpret this Error Message"
date: 2008-03-02
forum: General Help
---

### Post by navneeth on 2008-03-02
```
navneeth@ubuntu:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libkutils.so.1: cannot open shared object file: No such file or directory

```

A somewhat similar error is show when I open the other KDE app. in computer, K3b.

```
navneeth@ubuntu:~$ k3b
k3b: error while loading shared libraries: libkparts.so.2: cannot open shared object file: No such file or directory

```

How can I get those applications to work? Thanks.

---

### Post by es@urito on 2008-03-02
Have you ever tried to purge the amarok package and reinstall it?

---

### Post by navneeth on 2008-03-02
I did just that before creating this thread. But I've been having this problem for a couple of weeks now. Ever since there was an update for KDE-related files.

---

### Post by es@urito on 2008-03-02
install the following packages and tell me if it works:

kdelibs kdelibs4c2a kdelibs-bin kdelibs-data

It could be that some packages are missing due to an upgrade gone wrong

---

### Post by navneeth on 2008-03-02
I get this.

```
navneeth@ubuntu:~$ sudo apt-get install kdelibs kdelibs4c2a kdelibs-bin kdelibs-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdelibs4c2a is already the newest version.
kdelibs4c2a set to manual installed.
Package kdelibs-bin is a virtual package provided by:
  kdelibs4c2a 4:3.5.8-0ubuntu3.3
You should explicitly select one to install.
E: Package kdelibs-bin has no installation candidate

```

EDIT: I'm installing kdelibs-bin via Synaptic right now. Will update this in a few minutes.

---

### Post by navneeth on 2008-03-02
Nope. The error still shows up. :(

---

### Post by der_joachim on 2008-03-02
How about flushing your local settings? Go to the folder .kde/share/apps and rename the amarok folder. Having done that, start the amarok application and see if your problem persists. 

You'll lose your old settings, but perhaps you can use amarok again. 

As for your error message, it sounds as if it cannot see an external device like a MP3 player or a CDROM player or something. That is just speculation and utterly unfounded. 

Good luck.

PS Have you visited the amarok forums yet? They may be able to help you better than the Ubuntu crowd. See [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)

---

### Post by navneeth on 2008-03-03
> **der_joachim said:**
> How about flushing your local settings? Go to the folder .kde/share/apps and rename the amarok folder. Having done that, start the amarok application and see if your problem persists. 

You'll lose your old settings, but perhaps you can use amarok again. 

Nope.

```
navneeth@ubuntu:~/.kde/share/apps$ ls
amarok    drkonqi  kconf_update  khelpcenter  kstars   RecentDocuments
celestia  k3b      kcookiejar    konqueror    kwallet
navneeth@ubuntu:~/.kde/share/apps$ mv amarok amaroks
navneeth@ubuntu:~/.kde/share/apps$ ls
amaroks   drkonqi  kconf_update  khelpcenter  kstars   RecentDocuments
celestia  k3b      kcookiejar    konqueror    kwallet
navneeth@ubuntu:~/.kde/share/apps$ amarok
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libkutils.so.1: cannot open shared object file: No such file or directory

```

> As for your error message, it sounds as if it cannot see an external device like a MP3 player or a CDROM player or something. That is just speculation and utterly unfounded. 

Good luck.

I don't have an MP3 player, not do I use the CD ROM player much. 

> PS Have you visited the amarok forums yet? They may be able to help you better than the Ubuntu crowd. See [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)
I haven't yet. But thanks for pointing it out.

---

