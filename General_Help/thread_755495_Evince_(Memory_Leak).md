---
title: "Evince (Memory Leak?)"
date: 2008-04-14
forum: General Help
---

### Post by sfraim on 2008-04-14
Evince is using around 1.5 GB of memory whenever I view a pdf. 

I did some looking around, and this seems to be a (fairly) common problem dating back to about 2005. However, I did not find any solutions. I was wandering if this was normal? I am guessing not, and as I will be most surely looking at many PDF documents, where should I begin in finding a solution. 

Any help is appreciated.

Thanks!

---

### Post by IcemanV9 on 2008-04-15
Yikes! Are you sure it's using 1.5GB of RAM when you use evince??? A good way to check is in the terminal ...
```
top
```

---

### Post by sfraim on 2008-04-15
Yep :( , top shows evince using ~73% of my memory.

I have been messing around with my documents and it seems that the ones causing it are handwritten scans. My own PDF generated from LaTeX seem to be fine. 

Still 1.5GB seems a bit excessive!

---

### Post by IcemanV9 on 2008-04-17
Maybe you could check the bug report on evince to see if there is a workaround. And, you could try a different pdf reader, such as, adobe reader (for linux, of course), xpdf or pdf-viewer, to reduce the memory hogging for the time being.

---

