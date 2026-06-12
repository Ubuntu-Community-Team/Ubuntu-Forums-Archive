---
title: "libqt3-mt"
date: 2007-10-02
forum: General Help
---

### Post by Jvaldezjr on 2007-10-02
Recently this package (libqt3-mt) was updated in the repsositories, however when I tried to upgrade, I received this error message, and the package seems to be broken

How can I correct this, or at least let the person who uploaded it know there seems to be a problem?


```
(Reading database ... 134878 files and directories currently installed.)
Preparing to replace libqt3-mt 3:3.3.8really3.3.7-0ubuntu5.1 (using .../libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb) ...
Unpacking replacement libqt3-mt ...
dpkg: error processing /var/cache/apt/archives/libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb

```

---

### Post by dcstar on 2007-10-03
> **Jvaldezjr said:**
> Recently this package (libqt3-mt) was updated in the repsositories, however when I tried to upgrade, I received this error message, and the package seems to be broken

How can I correct this, or at least let the person who uploaded it know there seems to be a problem?


```
(Reading database ... 134878 files and directories currently installed.)
Preparing to replace libqt3-mt 3:3.3.8really3.3.7-0ubuntu5.1 (using .../libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb) ...
Unpacking replacement libqt3-mt ...
dpkg: error processing /var/cache/apt/archives/libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb

```

It may be that your download got corrupted, in a terminal try:

```
sudo rm /var/cache/apt/archives/libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb
sudo apt-cache gencaches
```

This should (hopefully!) delete the bad download and regenerate the cache list without it, and then run your Update Manager to download the package again.

---

