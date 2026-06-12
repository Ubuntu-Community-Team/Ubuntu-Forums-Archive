---
title: "update crashed - Error BrokenCount &gt; 0"
date: 2013-06-17
forum: General Help
---

### Post by rawlins02 on 2013-06-17
Running Ubuntu 12.04 on a Lenovo T60. Update crashed. Saw something related to Package Manager. I am no longer seeing updates come in. There is a red warning dot on top system bar. Clicking it says an error occured please run package manager.  Error BrokenCount > 0. But if I do

```

sudo apt-get install -f

``` 

I get output saying headers package getting installed and then this error:

```

Unpacking linux-headers-3.2.0-48 (from .../linux-headers-3.2.0-48_3.2.0-48.74_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-48_3.2.0-48.74_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-48/include/linux/bottom_half.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-48/include/linux/bottom_half.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-48_3.2.0-48.74_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


/usr partition has 1.8G available.  Any suggestions?  Could this be related to bad sources in my source.list file?

---

### Post by rawlins02 on 2013-06-18
A check of inodes

```

df -i

```

showed /usr partition at 100% full. I have removed several old linux images and header files and thus created more available space on the partition. Restarted and the error message from Package Manager is gone. Marking this as solved.

---

