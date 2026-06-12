---
title: "Maximum Hardware?"
date: 2008-07-10
forum: General Help
---

### Post by Rudedawg on 2008-07-10
Hey all, 
I'm building a new box that will hopefully turn into a dual/tri/or quad boot machine. I plan on using Intel's Quad core extreme QX6850 and 8Gb of pc8500 RAM. Is there any limitations for how much RAM Ubuntu will see? All versions of Windows have RAM limitations and I was wondering if Ubuntu did as well (hopefully not). 

Also, I'm still having problems with Intel's 965/x3100 graphics chipset on my laptop. I can't seem to get it to work properly in Ubuntu so that I can do more than just basic desktop effects. Any ideas?

---

### Post by sdennie on 2008-07-10
With 8G of RAM, you will either need to use the 64bit version of Ubuntu or, if you choose to use the 32bit version, use a kernel with PAE enabled.  The latter can be accomplished by installing and using the -server kernel or by compiling your own kernel but, it's probably best to use the 64bit version of Ubuntu.

---

### Post by Rudedawg on 2008-07-10
Awesome, thanks!

---

