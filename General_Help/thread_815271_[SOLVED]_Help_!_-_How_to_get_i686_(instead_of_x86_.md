---
title: "[SOLVED] Help ! - How to get i686 (instead of x86_64) when using wubi"
date: 2008-06-01
forum: General Help
---

### Post by vur246 on 2008-06-01
Hi all !

I have Dell XPS 410 with WinXP. I installed Ubuntu using Wubi, but I everything tot configured for AMD_64 while I have GenuineIntel Dual Core. Is it any way to enforce i686 installation when using Wubi ?

---

### Post by Vadi on 2008-06-01
But Dual Core can run 64bit, why would you want to go to 32bit?

---

### Post by ago on 2008-06-01
amd64 is fine for all 64 bit architectures including intel.

---

### Post by vur246 on 2008-06-01
Hi all !

Thanks a lot for you answers.
I am trying to compile an application and its makefile/scripts check for cpu and fail when they don't find i686. In addition I have problem with gcc compiler. I don't want to spend time digging into this environment and modifying it. It runs perfectly on Ubuntu   installed under VMware from i686 DVD image, I just wanted to have a native installation without dealing with manual partitioning.

So if it's a way to specify while running wubi that I don't want 64 bit ?

---

### Post by vur246 on 2008-06-01
Resolved.

It is explained in FAQ. My fault for not looking into FAQ before asking questions on forum

---

