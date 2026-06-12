---
title: "Missing lib file?"
date: 2016-05-18
forum: General Help
---

### Post by leslie-k on 2016-05-18
Dear friends,
I have installed Ubuntu 16.04 lts 64 bit on my i5 2.4g Samsung laptop. All appears ok.
I then 'installed' BBC BASIC for LINUX through the terminal (c/o Richard Russell). The install seemed to go ok.
The program will not run as it says file 'libGL.so.1' not found. The reason is simple - it isn't there.
Can anyone suggest how to get it?
Any advice would be appreciated.
... Leslie

---

### Post by Impavidus on 2016-05-18
On my system it's there. It's in /usr/lib/x86_64-linux-gnu/mesa/ and it's a symlink to libGL.so.1.2.0, both provided by the package libgl1-mesa-glx:amd64. It should be there. Maybe a linking problem? Maybe it's a 32 bit application? Even that should work, but you may have to install the 32 bit versions of some libraries.```
**$ dpkg --search libGL.so.1**
libgl1-mesa-glx:amd64: /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1
libgl1-mesa-glx:amd64: /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
**$ ls -l /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1**
lrwxrwxrwx 1 root root 14 apr 14 19:07 /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 -> libGL.so.1.2.0
```

---

### Post by haplorrhine on 2016-05-18
Given that Ubuntu can run right off of a flashdrive, couldn't leslie copy said file from said flashdrive (without needing to compile it from source code)?

---

