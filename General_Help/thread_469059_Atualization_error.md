---
title: "Atualization error"
date: 2007-06-09
forum: General Help
---

### Post by ahura on 2007-06-09
I have my ubuntu running perfectly, but, today it asked me to install:

linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic
linux-image-2.6.20.16-generic
linux-libc-dev

But, i received an error, i tried to reboot and try again, i tried #ubuntu on freenode, and nobody can help me out, this is what is happening:

E: /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb: não foi possível criar link de backup de `./boot/config-2.6.20-16-generic' antes de instalar nova versão

(My system was installed in Brazilian Portuguese, so i'll try to translate this error message: E: /var... ...i386.deb: Wasn't possible to create backup link of `./boot/config-2.6.20-16-generic' before installing newer version)

After it, it simply doesn't complete installation of linux-image-2.6.20-16-generic, and i'll copy the terminal message here:

Decompressing substitute linux-image-2.6.20-16-generic...
pkg: Error processing /var/cache/apt/archives/linux-image 2.6.20-16.generic_2.6
20-16.29_i386.deb (..unpack):
Wasn't possible to create backup link of ' ./boot/config-2.6.20-16-generic' before
installing newer version: Operation not permited
dpkg-deb: subprocess paste dead by signal (Broken Pipe)
Errors were found during processment of:
/var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
  Sub-process /usr/bin/dpkg returned an error code (1)
Instalation of a package failed. Trying to recover:

Thats it, and this message was poorly translated by me, because it is originaly in portuguese.

I believe problem is within boot directory, on #ubuntu, a guy trying to help me out and asked me to check my permissions on my /boot, i performed the command "ls -la /boot", and i don't know why, the guy said it was strange, that was when i said i had ubuntu running with Wubi, and he said he couldn't help me out because he don't know Wubi, so here i am back again to try to get a little help from you guys.

Please, HELP! :B

---

### Post by WhiteHorse on 2010-02-05
Is your disk full? Try:
```
df -h
```

---

