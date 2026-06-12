---
title: "I'm stuck: program central tries but fails to repair broken packages"
date: 2013-01-06
forum: General Help
---

### Post by koma77 on 2013-01-06
I tried to install google earth using the deb-package onto my Ubuntu 12.10 64-bit.

Apparently the installation failed leaving apt in a bad state.

If I start the program central it wants to repair a broken cache, but fails to do so.

Running sudo apt-get clean does not help.

Running sudo apt-get -f install gives me:

```
The following extra packages will be installed:
  libdv4:i386
Suggested packages:
  libdv-bin:i386
The following NEW packages will be installed:
  libdv4:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/65.2 kB of archives.
After this operation, 167 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 79707 package 'openshot-ffmpeg':
 error in Version string 'git-ab0189b-1': version number does not start with digit
(Reading database ... 439463 files and directories currently installed.)
Unpacking libdv4:i386 (from .../libdv4_1.0.0-4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdv4_1.0.0-4_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdv4/changelog.Debian.gz', which is different from other instances of package libdv4:i386
```

As it is now, I cannot install anything or remove anything...

What can I do to make apt forget about the libdv4:i386 package?

---

### Post by koma77 on 2013-01-06
I ran:

apt-get remove libdv4:i386 gstreamer0.10-plugins-good:i386 ia32-libs-multiarch:i386 ia32-libs

And it seemed to remove the broken cache thing.

But I cannot install ia32-libs after removing them. If I do, it tries to install libdv4:i386 gstreamer0.10-plugins-good:i386 ia32-libs-multiarch:i386 automatically and fails.

Maybe some more cleanup is needed?

---

### Post by ibjsb4 on 2013-01-06
Sounds like

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs](https://bugs.launchpad.net/ubuntu/+source/ia32-libs)

---

### Post by Us3r Unfriendly on 2013-01-06
dpkg --debug=400 --install Google earth package

---

### Post by koma77 on 2013-01-06
> **Us3r Unfriendly said:**
> dpkg --debug=400 --install Google earth package

That returns:

```
D000400:   checking group ...
D000400:     checking possibility  -> dpkg
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> lsb-core
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> ia32-libs
D000400:       not installed
D000400:         returning 0
D000400:     found 0
D000400:   found 0 matched 0 possfixbytrig -

```

---

### Post by iponeverything on 2013-01-06
Just remove the file that is causing this issue -- it is only a changelog ..

> sudo rm /usr/share/doc/libdv4/changelog.Debian.gz

---

