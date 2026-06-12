---
title: "Memory usage (page size)"
date: 2015-04-30
forum: General Help
---

### Post by mcsheffrey on 2015-04-30
I am running UBUNTU 15.04, 64 bit with 4GB of memory.
My question is even though my usage shows 2GB of memory used, the swap space is between 400-500 Mib.
Why would it use swap when there are 2 GB of memory available.

---

### Post by dino99 on 2015-04-30
only a supposition of my own: ureadahead may have use it at boot time, and then the swap is only cleared after a while (expected)
be sure your bios is set to 'remap' the ram to get full usage

---

### Post by v3.xx on 2015-04-30
Have you reset swappiness?

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Some processes use swap to store files no matter how much ram you have.  I have swappiness set to zero and this works for me, but most suggest a setting of 10.

---

### Post by mcsheffrey on 2015-05-03
Thanks for your replies, well it doesn't seem to be at boot time because its zero after startup. I set the swappiness to zero and it stlll climbed up to 750mb. Wasn't aware of this parameter, will do more experimenting, if I find anything I will post it.  Tks Roy

---

### Post by tgalati4 on 2015-05-03
Swap will generally be used when you near the limit of your RAM.  Those pages will remain in swap for as long as the machine is booted and they are not discarded to make room for more swap pages.  Normally this does not reduce performance.  If you use Firefox or Google-chrome with lots of tabs, expect RAM to be used quickly and swap to be filled just as quickly.

---

### Post by v3.xx on 2015-05-03
750M does not sound bad for Unity.  As said above, your browser will eat ram up in no time and my findings shows chrome is the biggest user of ram.  Maybe take a look at top.
```
top
```
Another thing I have found is proprietary video drivers can reduce system load.

Edit..
Misread your post

---

### Post by grahammechanical on 2015-05-03
I only have 1 GB RAM and at the moment with only Firefox loaded with only Ubuntu forums opened, System Monitor is showing 605 MiB RAM used and 28 MiB swap used.

Think of the OS as marking swap space in advance of the need to use it as a way of avoiding delay. The more RAM an OS has to use the more RAM it will use. And why not? What else is going to use memory than the OS? In a similar fashion the OS will claim swap space in consideration of the amount of RAM being used. It does not mean that any data is actually being paged to disk. It is just preparing in advance of a need.

This is how I understand it. I may not be scientifically accurate but I am certainly not troubled by this either.

Regards.

---

