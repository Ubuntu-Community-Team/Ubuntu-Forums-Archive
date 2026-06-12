---
title: "k3b installation - weird errors"
date: 2004-11-09
forum: General Help
---

### Post by TravisNewman on 2004-11-09
I'm in Hoary, but it doesn't seem the KDE packages have changed, so I posted here. Here's my output when trying to install k3b:

```
Preconfiguring packages ...
Selecting previously deselected package kdebase-bin.
(Reading database ... 95193 files and directories currently installed.)
Unpacking kdebase-bin (from .../kdebase-bin_4%3a3.2.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package kdebase-data.
Unpacking kdebase-data (from .../kdebase-data_4%3a3.2.2-1ubuntu2_all.deb) ...
Unpacking kcontrol (from .../kcontrol_4%3a3.2.2-1ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/fileshareset', which is also in package kdelibs-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package k3b.
Unpacking k3b (from .../k3b_0.11.17-1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
travis@eniac:~ $
```

---

### Post by jdong on 2004-11-09
```

dpkg: error processing /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/fileshareset', which is also in package kdelibs-bin

```

Translating from debian-ese:
```

The file /usr/bin/fileshareset already exists; it was installed by package kdelibs-bin. This new package, kcontrol, is trying to overwrite the file... I'll abort mission to prevent any potential corruption / data loss / damage!

```

The quick workaround is:
```

dpkg --force-overwrite --install /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb
```

If more errors show up, groan, get frustrated, then go for overkill:
```

dpkg --force-all --install /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb
```

---

### Post by TravisNewman on 2004-11-09
yeah, I knew the translation, just not the workaround. Thanks :)

---

