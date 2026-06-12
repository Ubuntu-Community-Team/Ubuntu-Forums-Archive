---
title: "Is this RAM consumption normal?"
date: 2008-05-09
forum: General Help
---

### Post by Fergalator on 2008-05-09
I thought Hardy required 384MB of RAM, so why does System Load tell me that 1.7 GB of my RAM is being used? (I only have Opera, Kopete and System Load on right now, I also have 2GB of RAM).

This is ridiculous, even Vista don't hog this much..

---

### Post by tamoneya on 2008-05-09
what is the output of ```
free -m
```

---

### Post by kpkeerthi on 2008-05-09
> **Fergalator said:**
> I thought Hardy required 384MB of RAM, so why does System Load tell me that 1.7 GB of my RAM is being used? (I only have Opera, Kopete and System Load on right now, I also have 2GB of RAM).

This is ridiculous, even Vista don't hog this much..

You may want to read about [the secret behind memory management in linux]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management").

---

### Post by Sef on 2008-05-09
> I thought Hardy required 384MB of RAM, so why does System Load tell me that 1.7 GB of my RAM is being used? (I only have Opera, Kopete and System Load on right now, I also have 2GB of RAM).

Basic explanation: GNU/Linux works by taking all of the memory and giving it out as it is needed.

---

### Post by Fergalator on 2008-05-09
[PHP]             total       used       free     shared    buffers     cached
Mem:          2026       1814        211          0        136        879
-/+ buffers/cache:        798       1227
Swap:          517          0        517
[/PHP]

woah, it's reaching 1.8 GB!

---

### Post by tamoneya on 2008-05-09
read the article it is very important.  Most of your memory is being used as cache and will be freed if you ever need it.  The command you ran shows that you are actually only using 798MB with 1227 MB free (second line)

---

### Post by Fergalator on 2008-05-09
> **Sef said:**
> Basic explanation: GNU/Linux works by taking all of the memory and giving it out as it is needed.

> **kpkeerthi said:**
> You may want to read about [the secret behind memory management in linux]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management").

That explains why the RAM is almost dried up, thanks.

---

