---
title: "Intel Quad Core and 4 Gb of RAM fully used?"
date: 2008-02-23
forum: General Help
---

### Post by Ziggurat on 2008-02-23
Hi, i am about to set up a system with an Intel Quad Core and 4Gb of RAM. Can anyone tell me if ubuntu will recognize this and install a kernel with SMP and the extension that supports the 4gb? Or i have to compile it myself? Thanks!!

---

### Post by Yes on 2008-02-23
You'll have to use the 64 bit version for Ubuntu to recognize all 4 Gb of ram.  You can download this just like the normal 32 bit version, you won't need to compile it or anything.

The standard Linux kernal now has SMP, so you won't need to do anything special for your quad core.

---

### Post by Ziggurat on 2008-02-23
Thanks! I have read that there is an extension for the 32 bit kernel that allows to use 4 gb of RAM, do you know anything about this?

The extension [SIZE=-1]Physical Address **Extensions** (PAE).[/SIZE]

---

### Post by psycardis on 2008-03-07
You shouldn't have to install the 64bit version of Ubuntu if I [understand correctly]("http://ubuntuforums.org/showthread.php?t=25684") 

From what I can tell it looks like you should be able to just install the SMP kernel I think i read [somewhere else]("http://ubuntuforums.org/showthread.php?t=591615&highlight=smp+bigsmp&page=4") something about a BIGSMP kernel (BIG meaning it has Physical Address Extension (PAE) enabled.

(please correct me if I'm wrong)

Psycardis

---

### Post by fjgaude on 2008-03-07
At this point I am hard pressed to understand why anyone would want to use 32-bit OS on their 64-bit machine. Everything is good in 64-bit in Ubuntu, and has been since Gutsy, 7.10.

Is there a 32-bit Linux program you know that isn't 64-bit?

---

