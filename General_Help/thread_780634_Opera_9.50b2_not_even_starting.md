---
title: "Opera 9.50b2 not even starting"
date: 2008-05-03
forum: General Help
---

### Post by Zorael on 2008-05-03
I'm running Kubuntu 8.04 x64 and I thought I'd try out Opera, mostly since it's Qt-based but also because Firefox somehow skyrockets to 100% cpu usage on sites with a lot of links.

There are no x64 packages for Opera so I installed it and with --force-architecture, but when installed it won't start.
```
zorael@sunspire:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.50-20080422.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64
```
libjvm and libawt definitely sound Java-related.

Any ideas?


edit: To elaborate on the Firefox complaint, some pages with tag clouds can seriously take 40 seconds to load, during which time Firefox uses 100% cpu and is completely unresponsive. Both FF2 and FF3 behave as such.

---

### Post by Zorael on 2008-05-03
Well, at least it loaded when I installed the not-linked-towards amd64 version.

[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/)

Not surprisingly, Java doesn't seem to work.

---

