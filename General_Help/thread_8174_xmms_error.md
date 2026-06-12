---
title: "xmms error"
date: 2004-12-14
forum: General Help
---

### Post by GeneticFreek on 2004-12-14
I installed xmms with synaptic from universe. But I get the following error:

> $ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!
 
Any ideas what I need to do to get xmms running?

---

### Post by wulf on 2004-12-15
I installed libmikmod, which you can find by searching in Synaptic. The error didn't seem to affect the operation of XMMS but I like to keep things tidy.

Presumably that means the XMMS package needs updating to include the dependency?

Wulf

---

### Post by adbak on 2004-12-15
Libmikmod2 is only needed for mp3 playback.  My guess is that you tried to play one or another copryrighted formats.  Therefore, XMMS needs that pkg only to play copyrighted music formats.

---

### Post by stijnb on 2005-02-22
Hi,

I had the same prob with the install of xmms :)  It's fixed now.

Do u have universe enabled? and run apt-get update and apt-get upgrade?

else it's just

(as user) sudo apt-get install libmikmod2

After doin this it worked.

plz let me now if it worked k? :)

hope it helps

---

### Post by botezatdi8435 on 2007-05-15
> **adbak said:**
> Libmikmod2 is only needed for mp3 playback.  My guess is that you tried to play one or another copryrighted formats.  Therefore, XMMS needs that pkg only to play copyrighted music formats.


[chemistry food science Loans plants plants](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

### Post by _pedja_ on 2007-05-17
I'm new to Ubuntu so don't laugh :)
i can't get pass this problem

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xmms-1.2.10

```

---

