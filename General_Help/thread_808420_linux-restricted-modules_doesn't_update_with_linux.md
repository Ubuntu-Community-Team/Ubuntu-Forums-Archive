---
title: "linux-restricted-modules doesn't update with linux-image-2.6.24-17-generic"
date: 2008-05-26
forum: General Help
---

### Post by robackja on 2008-05-26
Ubuntu Hardy

Why doesn't linux-restricted-modules update with the new linux-image-2.6.24-17-generic? I updated through the GUI updater, then rebooted. X failed to load (ie no nvidia kernel module for new  kernel)

had to drop to console and manually apt-get linux-restricted-modules for newest kernel.. I don't remember having to do this with previous versions of ubuntu.. is this a bug or `works as intended' ??

---

### Post by tribaal on 2008-05-27
Same problem here for some reason... I don't know why this wasn't automatic like it used to...

Anyway, installing linux-restricted-modules fixed it for me.

- Trib'

---

### Post by Monicker on 2008-05-27
Hrmm. The update installed the appropriate linux-restricted-module for me automatically.

EDIT:

From my synaptic logs

```
Commit Log for Mon May 26 08:59:53 2008


Upgraded the following packages:
apport (0.108.1) to 0.108.2
apport-gtk (0.108.1) to 0.108.2
gdm (2.20.6-0ubuntu1) to 2.20.6-0ubuntu2
gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
libgnome-keyring0 (2.22.1-1) to 2.22.1-1ubuntu1
libpam-gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
linux-generic (2.6.24.16.18) to 2.6.24.17.19
linux-headers-generic (2.6.24.16.18) to 2.6.24.17.19
linux-image-generic (2.6.24.16.18) to 2.6.24.17.19
linux-libc-dev (2.6.24-16.30) to 2.6.24-17.31
linux-restricted-modules-common (2.6.24.12-16.34) to 2.6.24.12-17.36
linux-restricted-modules-generic (2.6.24.16.18) to 2.6.24.17.19
python-apport (0.108.1) to 0.108.2
python-problem-report (0.108.1) to 0.108.2
```

---

### Post by TheAL76 on 2008-05-27
Just a guess, but perhaps you had the linux-restricted-modules version specific copy installed.

I had to install the linux-restricted-modules-server for 2.6.24-17, but I noticed there's one that says it has the latest version instead of the specific version.

---

### Post by chrisccoulson on 2008-05-27
Worked for me. My guess is you're missing the linux-generic meta-package

---

### Post by FAJALOU on 2008-12-21
I know that this is old, but the same thing happens to me during kernel updates.  I always end up going into Synaptic and installing linux-restricted-modules(uname -r).  How can this be fixed?

---

