---
title: "Conky Laptop-mode"
date: 2008-06-07
forum: General Help
---

### Post by chunchengch on 2008-06-07
I can use variable $laptop_mode to display status of laptop mode in numbers, such as 0 is off and 2 is on, but how can I display it with just "On" and "Off" instead of numbers? 

I searched all the conky variables and tested some of them, but found no one available, hope someone can teach me how to make it, thanks a lot.


[ATTACH]73243[/ATTACH]

---

### Post by cammin on 2008-06-09
try replacing **${laptop_mode}** with
**${if_existing /proc/sys/vm/laptop_mode 0}Off${else}On${endif}**

---

### Post by chunchengch on 2008-06-09
cammin,

Thank you!

I ever tried variable $if_existing many times, but never succeed, now I know I did not write the syntax right. thanks again!

---

