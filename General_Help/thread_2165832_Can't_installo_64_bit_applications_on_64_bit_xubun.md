---
title: "Can't installo 64 bit applications on 64 bit xubuntu, 32 bit applications work fine"
date: 2013-08-06
forum: General Help
---

### Post by bosbeemer on 2013-08-06
I recently installed the 64 bit version of xubuntu 12.04. While uname indicates it is the 64 bit version, I haven't been able to install 64 bit version of applications on my machine. I tried synergy and eclipse and in both cases only the 32 bit version worked fine. In case of synergy the 64 bit deb complained of incorrect architecture and 64 bit eclipse didn't run at all. I have 8 Gb RAM which is not possible with 32 bit, so I am very confused.

file indicates that the executables are 32 bit. 

Does anyone know what's going on?

```
 
>uname -a
Linux name 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

>file /usr/bin/file  
/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=0xabca77787115d8fb7fc615cc7f245660248f2625, stripped

```

---

