---
title: "[SOLVED] Help installing &amp;quot;source package 'Linux' in Ubuntu&amp;quot;"
date: 2008-05-17
forum: General Help
---

### Post by BandD on 2008-05-17
I'm trying to get my Texas Instrument Memory Stick Pro card reader working under Hardy.  

I read through bug report [#137686]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137686") and there is a fix in the very last post that takes me to [this page]("https://edge.launchpad.net/ubuntu/+source/linux/").  

The one I'm interested in is 2.6.24-16.29.  How do I 'install' this patched kernel?

---

### Post by Xiong Chiamiov on 2008-05-17
Do you need that specific kernel, or just a newer one that what you have?

Looking through apt, I see packages for 2.4.27-xx.

---

### Post by BandD on 2008-05-17
This kernel contains a specific patch to the tifm module.  I don't see this listed in apt.  But I've never really done any kernel stuff, so I'm a little nervous to just go for it.


EDIT:

I found a less 'intrusive' patch in this bug report:  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")

---

