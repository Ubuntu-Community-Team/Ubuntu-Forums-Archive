---
title: "seeking to understand!"
date: 2007-10-26
forum: General Help
---

### Post by lattmau on 2007-10-26
hi, i'm new to all this, but i finally got 3d acceleration to work (atleast i think i did because compiz works.  is there another way to check?)

but heres my situation:

i enabled the restricted nvidia legacy drivers for my old geforce2 ti card.  then i installed **nvidia-settings** and that caused problems and gave me some error messages.

next i tried removing nvidia-settings and installed **nvidia-xconfig** and that somehow resolved everything. (ie compiz works).  

THEN, i try installing nvidia-settings to see if it would work now, but when i try, it tells me i have to remove nvidia legacy driver (i think?) -- i didnt end up going through with this part


bottom line:  whats the difference between **nvidia-settings** and **nvidia-xconfig** and their functions? 

i'm happy it all works now, but i want to understand how it all works. thanks!

---

### Post by ddrichardson on 2007-10-27
nvidia-settings communicates with the driver using the NV-CONTROL X extension. nvidia-xconfig doesn't - it manipulates config files in X.

---

### Post by lattmau on 2007-10-29
are nvidia-settings and nvidia-xconfig two different methods of achieving the same end goal?

and can someone explain (or point me somewhere) how video is managed in linux? (ie, what are the different files that govern video and how they affect one another?, etc..)

---

### Post by ddrichardson on 2007-10-29
Basically yes. How do you mean video - X or like mpeg etc,.?

---

### Post by lattmau on 2007-10-29
i mean X

---

### Post by ddrichardson on 2007-10-29
[http://www.x.org/wiki/Development?action=show&redirect=DevelopersPages](http://www.x.org/wiki/Development?action=show&redirect=DevelopersPages)

---

