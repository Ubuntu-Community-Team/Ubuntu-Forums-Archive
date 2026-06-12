---
title: "Has anyone managed to install ClamAv 0.93 from source?"
date: 2008-05-02
forum: General Help
---

### Post by jingo811 on 2008-05-02
I've compiled before but I still don't get how to do it correctly it's like rolling a dice you never know for sure what you get.  This time I'm trying to install Clamav since Synaptic complains about it when I try to update the virus definitions and try to scan one small file.

I follow these instructions.  And after I "./configure" I get these error messages which makes it impossible for me to run "make" and "make install".
Judging by the errors does this mean that I can't install ClamAv 0.93 from source or do I just lack in knowledge?
[http://wiki.clamav.net/Main/InstallFromSource](http://wiki.clamav.net/Main/InstallFromSource)

```
configure: error: Please install zlib and zlib-devel packages
```

```
bill@gates:~/temp/clamav-0.93$ **sudo apt-get install zlib zlib-devel**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zlib
```

---

### Post by jingo811 on 2008-05-02
Ah found the problem why doesn't the SourceForge progamming authors and the Ubuntu repository guys communicate better so the libraries are named the same :confused:
```
bill@gates:~/temp/clamav-0.93$ **sudo apt-cache search zlib | grep ^zlib "--color=auto"**
[COLOR="Red"]zlib[/COLOR]1g - compression library - runtime
[COLOR="Red"]zlib[/COLOR]1g-dev - compression library - development
[COLOR="Red"]zlib[/COLOR]-bin - compression library - sample programs
[COLOR="Red"]zlib[/COLOR]c - Uncompressing C Library

```

---

