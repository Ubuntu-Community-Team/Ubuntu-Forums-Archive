---
title: "Serious Apt error"
date: 2004-10-31
forum: General Help
---

### Post by oddabe19 on 2004-10-31
```
root@ubuntu:/home/oddabel/Desktop # apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavcodec2
The following NEW packages will be installed:
  libavcodec2
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B/1036kB of archives.
After unpacking 2580kB of additional disk space will be used.
Do you want to continue? [Y/n] y

Preconfiguring packages ...
(Reading database ... 150599 files and directories currently installed.)
Unpacking libavcodec2 (from .../libavcodec2_1%3a0.4.9-pre1-0.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavcodec2_1%3a0.4.9-pre1-0.2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libavformat.so.0.4.9-pre1', which is also in package libavformat0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec2_1%3a0.4.9-pre1-0.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/oddabel/Desktop #
```

That's it. I mean, I was trying to get the new mplayer-plug in, and that package.. just... well... broke... it's not installed... so i can't do anything till i fix it... and it just  won't fix.

Has anyone else gotten this?

---

### Post by jdong on 2004-10-31
Use **dpkg --force-all --install /var/cache/apt/archives/this-package-is-bitching.deb**

---

### Post by oddabe19 on 2004-10-31
duh... stupid me... that makes sense... thanks  ](*,)

---

