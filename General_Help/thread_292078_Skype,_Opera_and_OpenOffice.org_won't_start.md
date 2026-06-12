---
title: "Skype, Opera and OpenOffice.org won't start"
date: 2006-11-03
forum: General Help
---

### Post by humansuit on 2006-11-03
Hello, 

I'm having a really annoying problem. Skype, Opera and OpenOffice won't start everytime i try to open them. They crash at startup with floating point exception maybe every third time I try to open them. I'm using Edgy, but this happened with Dapper also (with Opera and skype, not with openoffice iirc)

This is what happens when I try to open them from terminal:

```
koti@bunmaster:~$ skype
Floating point exception (core dumped)

koti@bunmaster:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Floating point exception (core dumped)


koti@bunmaster:~$ openoffice 
/usr/lib/openoffice/program/soffice: line 254:  6110 Floating point exception"$sd_prog/$sd_binary" "$@"

** (process:6094): WARNING **: Unknown error forking main binary / abnormal early exit ...
```

Any ideas? Broken library? Melted processor? There could be other programs which do the same, i just haven't used them recently..

Thanks for any help

---

### Post by tja on 2006-11-04
maybe [this]("http://www.ubuntuforums.org/showthread.php?t=293081")

---

### Post by humansuit on 2006-11-05
Hmm maybe.  xdpyinfo |grep dimensions did report false dimensions for me and running sudo dpkg-reconfigure xserver-xorg seemed to have fixed it. Everything runs fine now, thanks!

---

