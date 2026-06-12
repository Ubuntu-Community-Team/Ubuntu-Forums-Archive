---
title: "what does uname's resualts mean"
date: 2008-01-18
forum: General Help
---

### Post by salah_tr on 2008-01-18
Hi all,
I tried the fellowing commands 
```
uname -r
```
result : 
 ```
2.6.22-14-generic
```
what does **-14-generic** mean :?:
```
uname -v
```
result : 
 ```
#1 SMP Sun Oct 14 23:05:12 GMT 2007
```
what does that result mean :?:
cheers
Salah

---

### Post by mrazster on 2008-01-18
You can also use
```
uname -a
```
and you'll get everything in one command..like this:
```
username@username:~$ uname -a
Linux ubuntu 2.6.23.9 #1 SMP PREEMPT Sat Dec 1 11:10:59 GMT 2007 i686 GNU/Linux

```


As to your question:
*_generic_* means that your usin ubuntus "own" precompiled kernel.
*_SMP_* means that you are using a multicore compatible kernel...you got support fpr cpu with more than one core.
And the rest is time, date and year when the kernel was either compiled or installed...not really sure. In my example above it is when I compiled the kernel.

---

### Post by Sef on 2008-01-18
> And the rest is time, date and year when the kernel was either compiled or installed...not really sure. In my example above it is when I compiled the kernel.

I checked mine and that was when the new kernel was installed (2.6.22-14-generic for me.)

---

### Post by dcstar on 2008-01-18
> **salah_tr said:**
> Hi all,
I tried the fellowing commands 
```
uname -r
```
result : 
 ```
2.6.22-14-generic
```
what does **-14-generic** mean :?:
.........


The "-14-generic" is the version of the kernel you have running, there are a few different versions available in the repositories:

Server - a kernel optimised for server based use.
rt - a kernel optimised for "Real Time" audio processing applications.
generic - a kernel optimised for graphical desktop/general use (best for most users).

Kernels are under constant development, the current one is 2.6.24.rc8 and a stable version of this may appear in Ubuntu 8.04 when that is released in April.

---

### Post by salah_tr on 2008-01-20
Thanx everyone

---

