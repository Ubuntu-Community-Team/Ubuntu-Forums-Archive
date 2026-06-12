---
title: "low graphics mode and no network on 3.19.0-39-generic"
date: 2015-12-26
forum: General Help
---

### Post by jj4 on 2015-12-26
I ran an sudo a-get update the other day but now when I start I have low graphics mode and no internet.

Recovery mode does not work either and the graphics cannot be repaired, I tried reinstalling gdm.

The only thing that works is for me to go into advanced options on startup and select the previous versin 3.13.0-66-generic,

Any ideas how I can fix this or remove the 3.19.0-39 version?

---

### Post by QIII on 2015-12-26
Hello!

Did you have a proprietary graphics driver installed at the time you did the update?  If so, how had you installed it?

---

### Post by jj4 on 2015-12-26
> **QIII said:**
> Hello!

Did you have a proprietary graphics driver installed at the time you did the update?  If so, how had you installed it?

No, nothing proproetary, it was all working from the standard install.
Now, I have firther problems with trying to install virtualbox as it doesn't recognise the kernel because I started from themenu an older version.

```

j@j-Aspire-5610:/etc/init.d$ sudo apt-get install linux-headers build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-3.19.0-18-lowlatency 3.19.0-18.18
  linux-headers-3.19.0-18-generic 3.19.0-18.18
  linux-headers-3.19.0-42-lowlatency 3.19.0-42.48
  linux-headers-3.19.0-42-generic 3.19.0-42.48
  linux-headers-3.19.0-41-lowlatency 3.19.0-41.46
  linux-headers-3.19.0-41-generic 3.19.0-41.46
  linux-headers-3.19.0-39-lowlatency 3.19.0-39.44
  linux-headers-3.19.0-39-generic 3.19.0-39.44
  linux-headers-3.19.0-37-lowlatency 3.19.0-37.42
  linux-headers-3.19.0-37-generic 3.19.0-37.42
  linux-headers-3.19.0-33-lowlatency 3.19.0-33.38
  linux-headers-3.19.0-33-generic 3.19.0-33.38
  linux-headers-3.19.0-32-lowlatency 3.19.0-32.37
  linux-headers-3.19.0-32-generic 3.19.0-32.37
  linux-headers-3.19.0-31-lowlatency 3.19.0-31.36
  linux-headers-3.19.0-31-generic 3.19.0-31.36
  linux-headers-3.19.0-30-lowlatency 3.19.0-30.34
  linux-headers-3.19.0-30-generic 3.19.0-30.34
  linux-headers-3.19.0-28-lowlatency 3.19.0-28.30
  linux-headers-3.19.0-28-generic 3.19.0-28.30
  linux-headers-3.19.0-26-lowlatency 3.19.0-26.28
  linux-headers-3.19.0-26-generic 3.19.0-26.28
  linux-headers-3.19.0-25-lowlatency 3.19.0-25.26
  linux-headers-3.19.0-25-generic 3.19.0-25.26
  linux-headers-3.19.0-23-lowlatency 3.19.0-23.24
  linux-headers-3.19.0-23-generic 3.19.0-23.24
  linux-headers-3.19.0-22-lowlatency 3.19.0-22.22
  linux-headers-3.19.0-22-generic 3.19.0-22.22
  linux-headers-3.19.0-21-lowlatency 3.19.0-21.21
  linux-headers-3.19.0-21-generic 3.19.0-21.21
  linux-headers-3.19.0-20-lowlatency 3.19.0-20.20
  linux-headers-3.19.0-20-generic 3.19.0-20.20
  linux-headers-3.19.0-16-lowlatency 3.19.0-16.16
  linux-headers-3.19.0-16-generic 3.19.0-16.16
  linux-headers-3.19.0-15-lowlatency 3.19.0-15.15
  linux-headers-3.19.0-15-generic 3.19.0-15.15
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate
j@j-Aspire-5610:/etc/init.d$ 


```

---

