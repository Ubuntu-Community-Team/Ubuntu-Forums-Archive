---
title: "Getting rid of older kernels"
date: 2006-07-26
forum: General Help
---

### Post by Lucidio on 2006-07-26
Im impressed that everytime i made a kerenel update suggested for the update manager, the list of kernels in grub increase. I supose that all of them are ocuping space disk in my system.
how can i get rid of the older kernels i have?

:?:

---

### Post by JoWilly on 2006-07-26
Start synaptic and remove them.... (search for linux-image, linux-restricted-modules, linux-headers,...)

But don't remove your latest kernel if you want your system to boot !

---

### Post by Lucidio on 2006-07-26
thanks man! that really help!
everithing go flawless!:D 

Thank God for the UBUNTU COMMUNITY!

---

### Post by Kingsley on 2006-07-26
i made a search for linux-image and got:

alsa-base
linux-image-2.6.15-23-386
linux-image-2.6.15-25-386
linux-image-2.6.15-26-386
linux-image-386

which are safe for me to remove? :s

---

### Post by aysiu on 2006-07-26
Remove 23 and 25. Make sure you are booted into 26 before you do this. You shouldn't remove a kernel you're using.

---

