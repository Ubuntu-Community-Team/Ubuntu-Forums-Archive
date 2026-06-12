---
title: "Kernel issue"
date: 2007-06-07
forum: General Help
---

### Post by Perfex on 2007-06-07
Heres what is going on.. awhile ago I installed one of the kernel updates.. seemed to work fine then by my fault or something else ndis wrapper and synaptics touchpad stopped working, I tried to make ndis wrapper work again in it .. with no luck.

So I selected the older kernel to boot from in the grub menu.. and everything works.. hmm?
And recently I succeeded in installing ati/beryl and got it working wonderful..

heres the question how can I remove  old kernel not only from the grub but from the system?
 will it have any adverse affects?

Thanks for any assistance in advance

---

### Post by hardyn on 2007-06-07
use synaptic, and remove the headers, image, and restricted packages; but pay attention to the version number.

---

### Post by NeoLithium on 2007-06-07
If you don't have the touchpad and wrapper working, you might want to be cautious about removing the old kernel though, just a thought.

---

### Post by Perfex on 2007-06-07
Thanks for the reply .. I did not realize it would be that easy.. as far as the kernels I am removing the new one.. the old one works

---

### Post by Perfex on 2007-06-07
Well it worked but now my xgl session seems broke.. loads up all destorted :(

---

