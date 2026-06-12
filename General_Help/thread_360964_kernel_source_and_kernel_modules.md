---
title: "kernel source and kernel modules"
date: 2007-02-13
forum: General Help
---

### Post by luke9511 on 2007-02-13
ok i need to update my video card drivers in ubuntu 6.10 edgy and before i can do that i need the kernel source and kernel modules yet i cant figure out how to get them, can anyone help me out? thanks in advance for any help/advice

---

### Post by machoo02 on 2007-02-13
Just out of curiosity, why do you need the kernel source?  If you are trying to install the proprietary Nvidia or ATI drivers, all you need is the linux-restricted-modules package```
sudo aptitude install linux-restricted-modules-
```
add either 386 or generic on to the end of that command depending upon which kernel you are running.

---

### Post by luke9511 on 2007-02-13
well i dont have nvida on my laptop just a intel graphics chip, i posted a thread about having problems installing updated drivers so that i can play guildwars through cedega, but before i can i have to install the updated drivers and since i get a error  with something about the kernel, then im guessing this is what i need, atleast i hope so

---

### Post by luke9511 on 2007-02-15
so can anyone tell me how to get the kernel modules and kernel source?

---

