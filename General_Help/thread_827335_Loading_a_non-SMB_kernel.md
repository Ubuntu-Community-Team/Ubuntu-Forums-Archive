---
title: "Loading a non-SMB kernel?"
date: 2008-06-12
forum: General Help
---

### Post by squishyalt on 2008-06-12
I didn't know where to ask this, so I'm asking here.

I was having an issue with a software package and the author said that i may want to run with a non-SMP kernel until they release a fix.

What does that mean, and how do I do it?

---

### Post by kidders on 2008-06-14
Hi there,

That means the program is probably having multithreading issues. The author's suggested fix is to remove your Linux's ability to run on more than one CPU.

Assuming you have a multi-core processor, this probably isn't something you'll want to do ... you'd be crippling your entire OS for the sake of one application. I would suggest ...```
$ uname -v
#1 SMP Tue Feb 12 03:10:53 UTC 2008
```You might as well double-check that you really are running an SMP-enabled kernel. If you don't know how many processors you have, try ...```
$ grep ^processor /proc/cpuinfo | wc -l
4
```Depending on the answer, you have a few options:[LIST]
[*]If you only have one CPU, there's no particular reason to enable SMP at all. In fact, it can be safer not to.
[*]If you have more than one, you might want to install both a unicore kernel *and* an SMP-enabled one, so you can switch between them at boot.
[*]Alternatively, I suppose you could virtualise your buggy app. That would be an awful lot of effort though!
[/LIST]

To install a non-SMP kernel, I would rebuild my current one with CONFIG_SMP turned off. I'm not aware of a faster way ... but someone else might be.

---

