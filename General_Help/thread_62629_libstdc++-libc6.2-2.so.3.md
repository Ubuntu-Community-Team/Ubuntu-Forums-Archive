---
title: "libstdc++-libc6.2-2.so.3 ?"
date: 2005-09-05
forum: General Help
---

### Post by guice on 2005-09-05
I'm trying to get Synergy2 installed, and I'm getting an error trying to start up the server:
```
synergys: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

I've installed libstdc++6 and libstdc++6-dev, but I'm still getting the erorr. An ls within /usr/lib does not reviel the requried libstdc's: ```
root@kiler:/usr/lib # ls libstdc*
libstdc++.so.5  libstdc++.so.5.0.7  libstdc++.so.6  libstdc++.so.6.0.4
```
Know where I can get this library? Which package do I need to install to insure it's installed?

I found an ooooold newsgroup posting point me to: [http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179) but alas that URL is no longer valid.

Thanks

---

### Post by odin on 2005-09-05
I still have another libstdc++6 package (libstdc++6-pic) try  this.Because it says something about shared libraries and it may be something like.If you cant find it post it and I'll post my sources.list.

---

### Post by guice on 2005-09-05
[QUOTE=odin]I still have another libstdc++6 package (libstdc++6-pic) try  this.Because it says something about shared libraries and it may be something like.If you cant find it post it and I'll post my sources.list.[/QUOTE]
 I don't have such a package avaliable:```
root@kiler:~ # apt-cache search libstdc
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++5 - The GNU Standard C++ Library v3
libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
root@kiler:~ #
```

---

### Post by banjobacon on 2005-09-05
Install libstdc++2.10-glibc2.2

---

### Post by guice on 2005-09-05
[QUOTE=banjobacon]Install libstdc++2.10-glibc2.2[/QUOTE]
 ```
root@kiler:~ # apt-get install libstdc++2.10-glibc2.2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc++2.10-glibc2.2
root@kiler:~ #
```No such package. Using Kubuntu if that made any difference.

*Edit; however, I did goto Debian's site and found the pakage there and installed it just fine. Synergy2 is now back fully operational! Thanks!

---

### Post by adam.mech09 on 2006-03-10
hey

just tried with apt, worked fine for me...

-Adam

---

### Post by airtonix on 2006-04-25
yeah me too i fink......at least the problem with required libstdc++2.10-glibc2.2 isn't cropping up anymore....no i have to configure the ting....how lovely

---

