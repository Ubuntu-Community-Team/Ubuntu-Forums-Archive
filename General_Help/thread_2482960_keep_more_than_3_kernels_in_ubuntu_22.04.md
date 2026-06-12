---
title: "keep more than 3 kernels in ubuntu 22.04?"
date: 2023-01-15
forum: General Help
---

### Post by habernir on 2023-01-15
hello

i know that ubuntu keep only 3 kernels and autoremove was added to apt
but i want to ask if it possible to change that to keep more than 3 kernel , because i'm using also xanmod kernel 

thanks 
nir

---

### Post by TheFu on 2023-01-17
I've had 5+ kernels. I suspect the default limitation is for a since kernel line.  So, if you are running 4.15.x, 5.4.x, 5.10, 5.11, 5.15, and 6.0.x kernels, you could have 2x6 = 12 kernels using the default settings.

For people that use volume managers for our OS, a separate /boot/ partition is needed and it is common for too many kernels to cause out of space issues in /boot/.  These forums have lots of people with that issue.

I'm only seeing 2 kernels in /boot/ now, so I think the limit is 2 per line, but I run autoremove after patching to avoid a full /boot/ partition.

Have you tried specifically installing the kernel you want, not just using the kernel metapackage?

I know the 'mainline' kernel tool is outside the normal apt cleanup efforts too. Is that an option?

---

### Post by grahammechanical on 2023-01-17
I may be completely wrong on this but I think that if we update/upgrade using the terminal then old kernels do not get removed until we run apt autoremove. If we use Software Updater then autoremove is run after update and upgrade have run.

By not running autoremove a lot of packages will not get removed. Then when you want to remove all those not needed packages you will remove all the old kernels if you are not kernels.

Regards

---

### Post by ActionParsnip on 2023-01-18
Doesn't it keep them all but only show 3 in GRUB? Where is ths value of "kept" kernels set, please?

---

