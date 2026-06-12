---
title: "Gutsy 64bit only sees 3.8GB?"
date: 2008-03-14
forum: General Help
---

### Post by Aikon- on 2008-03-14
Hi everyone; I'm running a Lenovo T61. I am currently stuck with Vista (32bit) until the end of the semester, but then I will be dropping it for Ubuntu (64bit).

I have just upgraded from 2GB to 4GB of ram (knowing full-well my vista install won't see all of it). I booted into a 64bit Gutsy live-cd to check out the new memory, and to my surprise, System Monitor shows "User memory: 249.2 MB of 3.8 GB 6.4%".

Being 64bit, I expected Gutsy to see all 4GB of ram.. am I missing something?

FYI I am currently running Gutsy 32bit on my desktop with 1536MB of RAM installed, and system monitor on that shows 1.5GB (correct).

Enlighten me, please!

-Aikon

---

### Post by scragar on 2008-03-14
is it 4GiB or 4GB? there's a very important difference:
```
4GB  = 4*1024*1024*1024B = 4294967296B
4GiB = 4*1000*1000*1000B = 4000000000B
```
reversing that(estimated, calc got into some rounding errors, but it's enough for the point):
```
4000000000B = 3.726GB
```

---

### Post by Aikon- on 2008-03-14
Well, it's memory.. and as far as I am aware, memory has always been listed in GiB..?

According to *top*:

Mem:  3985800k total

Which, when you divide by 1024*1024 (to get GiB), = 3.8 GiB (I'm going to go ahead and assume System Monitor means GiB when they say GB).

**Edit**: If Gutsy could see all the memory, then top should tell me (4*1024*1024) = 4194304k total

---

### Post by scragar on 2008-03-14
memory is often sold in GiB and measured in GB, it's just the way manufactures can reduce costs that little bit more without having to adjust their scaling, system monitor and such all list it in GB, not GiB

---

### Post by Aikon- on 2008-03-14
> **scragar said:**
> memory is often sold in GiB and measured in GB, it's just the way manufactures can reduce costs that little bit more without having to adjust their scaling, system monitor and such all list it in GB, not GiB

No. You are thinking about hard-drives, not memory. Computer memory has always been sold, discussed, measured, etc. in the binary form of GB. I.e. when someone says "I have 2GB of RAM", they mean 2048MiB.

64MB, 128MB, 256MB, 512MB, 1024MB, 2048MB, 4096MB.. these are memory values, and they are all 2^x.

Regardless, your analysis still doesn't match the symptoms; you reach a value of 3.7GB, System Monitor lists 3.8. Top tells me 3985800k, which can either be kiB or kB; either way, it adds up to **less than** the 4096MiB I have installed.

**Edit** Let me be douple-plus ultra-clear: by **memory** I am referring to **RAM**, not storage capacity.

---

