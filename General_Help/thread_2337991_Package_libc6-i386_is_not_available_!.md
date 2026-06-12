---
title: "Package libc6-i386 is not available ?!"
date: 2016-09-23
forum: General Help
---

### Post by fairbird on 2016-09-23
I have ubuntu 12.04 32bit
```
No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

```
I need to install Package libc6-i386 but I can not ..

```
raed@fairbird:~$ sudo apt-get install libc6-i386Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6


E: Package 'libc6-i386' has no installation candidate
raed@fairbird:~$ 
```

any advice it?! 

Thank you

---

### Post by steeldriver on 2016-09-23
AFAIK libc6-i386 provides 32-bit versions of standard libraries for use on a 64-bit system

Since you have a 32-bit system, 32-bit versions of these libraries are provided natively by its regular libc6 package

Hence there is no 32-bit version of libc6-i386

---

### Post by fairbird on 2016-09-23
Ok... got it ..

Thank you

I will try to going to 64-bit ..

---

### Post by steeldriver on 2016-09-23
What is your end goal? *why *do you think you need libc6-i386?

Changing OS seems like a sledgehammer way to go about things

---

