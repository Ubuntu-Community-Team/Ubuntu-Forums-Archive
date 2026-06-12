---
title: "Kubuntu 6.10 on PIII 1.2 GHz and 512 MB RAM?!"
date: 2006-10-29
forum: General Help
---

### Post by Amorphous_Snake on 2006-10-29
I am currently running it on the same PC with 384 MB RAM. Will adding another 128 MB speed things up a little? 512 MB is the maximum allowed by my mobo. This is an extremely old PC and RAM upgrade is the only thing I can do for it!

I used to run Ubuntu, but I wanted to try Kubuntu, which looks nice by the way!

I forgot to say that I have 1.2 GB as swap, and with the current 384 MB RAM, I only have 5 MB free RAM.

---

### Post by reclusivemonkey on 2006-10-30
> **Amorphous_Snake said:**
> I am currently running it on the same PC with 384 MB RAM. Will adding another 128 MB speed things up a little? 512 MB is the maximum allowed by my mobo. This is an extremely old PC and RAM upgrade is the only thing I can do for it!

I used to run Ubuntu, but I wanted to try Kubuntu, which looks nice by the way!

I forgot to say that I have 1.2 GB as swap, and with the current 384 MB RAM, I only have 5 MB free RAM.

I you are using swap, your machine will be slow. Can you hear your hard drive working a lot when its slow?

---

### Post by Amorphous_Snake on 2006-10-30
As a matter of fact, Kubuntu 6.10 is working faster than Ubuntu 6.06 used to!

Although I see that only about 5-20 MB are free from my 384 MB RAM, the swap used is 0-100 KB! And I don't hear my HDD.

What have they done in Edgy?!!!

---

### Post by bmillsap on 2006-10-30
Are you quoting free memory before or after adjusting for the system cache usage?  I think the system will essentially always use whatever available memory there is for something.  The line that "free" outputs that adjusts for system cache usage will tell you what memory is actually committed to programs and processes as opposed to being used for caching.  This could be why you're seeing total memory usage but no swap file usage.

---

