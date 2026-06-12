---
title: "About Kernel Programming..."
date: 2007-08-13
forum: General Help
---

### Post by madhu542 on 2007-08-13
Hai,

I wrote a module to generate the Randam numbers, and I run the "make" command it also works fine and created the .ko and other files, But while I tried to install this module into my kernel with the command 'insmod rd.ko' it is giving me the error as...

"insmod: error inserting 'rd.ko': -1 File exists" some times and "Killed" sometimes . So,

I run the modinfo command it shows...

modinfo: could not find module rd

for dmesg also it is no information related to my module...

I am new bee...Plz help me...

Thank you.
Madhu.

---

### Post by jnorthr on 2007-08-13
try using super user to install modules, something like:
sudo insmod xxx

---

