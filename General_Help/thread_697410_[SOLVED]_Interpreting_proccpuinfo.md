---
title: "[SOLVED] Interpreting /proc/cpuinfo"
date: 2008-02-15
forum: General Help
---

### Post by Cadmus on 2008-02-15
I've got an old server which I've got Gutsy Server on, now I can pop the lid off and see how much memory it's got, but I can't do the same for cpu, I've done
```
cat /proc/cpuinfo
```
but I'm having a hard time figuring out what it means. Sadly the machine can't be connected to the internet so I can't give you the full printout easily but here's what I have so far that googling has told me might be pertinent:
[LIST=1]
[*]It is showing two processors
[*]Both have the same physical ID
[*]They have differing core IDs
[*]Both report having two cores
[*]Both report a model name of Intel(R) Xeon(R) CPU 3040 @ 1.86GHz
[*]Both have hyperthreading enabled
[/LIST]

If I've missed anything you need do ask :)

From what I understand this means I have a single processor with two cores, but when I pass this machine on I'd like to be sure I'm giving them the correct specs. All assistance appreciated.

---

### Post by tribble222 on 2008-02-15
I have one dual-core processor in my machine.  The output of that command for me gives two processors, same physical ID, different core IDs.  So it sounds like that's what you have.

But can't you just open the case and see if there are two processors or one?

---

### Post by Cadmus on 2008-02-15
Thanks for the comparison, I'm pretty confident it is a single dual-core processor

> **tribble222 said:**
> 
But can't you just open the case and see if there are two processors or one?

Tempting, but it's a 1U server in a fairly short chassis and it's a bit of a jigsaw in there, besides I could only really check by removing the heatsink, then there's a chance I might mess up the cooling.

---

