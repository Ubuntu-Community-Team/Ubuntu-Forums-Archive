---
title: "Error compiling STLPort"
date: 2007-01-12
forum: General Help
---

### Post by sandelz on 2007-01-12
Hi!

I have a problem compiling STLPort 5.1.0 on Xubuntu 6.10.
First I issue commands :
[LIST]
[*]./configure
[*]make -f gcc.mak depend
[/LIST]and the actual make 
[LIST]
[*]make -f gcc.mak install
[/LIST]
It starts to compile ok, but stops with error :
```

c++: crt{i,beginS}.o: No such file or directory
c++: crt{endS,n}.o: No such file or directory

```
Is there something I'm doing wrong?

---

### Post by po0f on 2007-01-12
sandelz,

STLport is [in the repos](http://packages.ubuntu.com/edgy/libdevel/libstlport5.0-dev), but it is only version 5.0.2.  If this is good enough for you, I'd suggest just installing it through Synaptic/aptitude.  Note that you will have to have the universe repos enabled to install it.

---

### Post by sandelz on 2007-01-12
Thanks for the information.

I need this for coding(d'oh) and I was asked to try 5.1.0 version of STLPort.

I'll install stlport from repos if there is no way to compile the new version but I would still be grateful if someone knows the solution to the problem.

---

### Post by phkoester on 2008-03-14
> **sandelz said:**
> Thanks for the information.

I need this for coding(d'oh) and I was asked to try 5.1.0 version of STLPort.

I'll install stlport from repos if there is no way to compile the new version but I would still be grateful if someone knows the solution to the problem.

Mhm, the q'n is already more than a year old, but here is a work-around for the problem: Make

SHELL := /bin/bash

the first line of `gcc.mak' in `/build/lib', and everything will compile and link fine.

The make file uses the curly-braces-file-name-expansion feature of `bash', which `sh' doesn't understand. The STLport make file erroneously assumes `sh' to be `bash', which isn't the case on all systems.

That should help
--Ph.

---

### Post by erik_boi on 2008-07-12
Thanks phkoester!
If it may not have helped the OP but I found it very useful =D>

---

