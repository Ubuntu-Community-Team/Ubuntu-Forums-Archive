---
title: "new kernel does not mount XFS"
date: 2007-04-06
forum: General Help
---

### Post by bjdekruif on 2007-04-06
Hello all, 

Although I am working for quite some time with the 2.7-11 kernel, it decided to stop mounting my XFS drive. I must have done something, but I have no clue what. 
After some looking around, I found that the XFS module was not loaded, and this one is needed for the mounting. 

However, even if I insert this module in the kernel, and mount the drive, gnome is not working as  I want, eg. my mouse is not working. I got the feeling that more modules are missing, or that something else is missing. 

On the other hand, if I use the 2.7-10 kernel, everything works. 

I was thinking of recompiling the kernel, as the system seems to work. Is this a good idea, or does anybody knows a better solution?

All pointers are appreciated

bas

---

