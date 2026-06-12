---
title: "My swap file stopped working"
date: 2006-12-31
forum: General Help
---

### Post by raul_ on 2006-12-31
I had my swap file working perfectly. Honestly i didn't need it, but i created just for fun :mrgreen:  so i followed the steps, created a swapfile in / and allocated 2 GB. Today i boot my computer and conky says "no swap" . So i tried to go to the terminal and activate and it says:

```

$ sudo swapon /swapfile 
swapon: /swapfile: Argumento inválido

```

that's "Invalid Argument" :-k any ideas?  What bugs me is that it was working perfectly...of course it was never used because i never run out of RAM (1 GB and i don't do many adventures)

---

### Post by raul_ on 2006-12-31
Maybe I should add that i switched from ext2 to ext3 yesterday, and i think it stopped working then

EDIT: I just created one again using the same file and now it works

---

