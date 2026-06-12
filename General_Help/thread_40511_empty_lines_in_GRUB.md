---
title: "empty lines in GRUB"
date: 2005-06-09
forum: General Help
---

### Post by zwaardmeester on 2005-06-09
Hi,

I wonder if it is possible to insert empty lines in the Grub boot menu. I have been searching for this in the documentation but got no results. What I want is something like:

<--->
Linux kernel blabla
Linux rescue
memtest

Other Operating Systems:

Windows XP
<--->

---

### Post by Pixel on 2005-06-09
in /boot/grub/grub.conf

There should be lines such as this...
```
title="your kernel here"
``` 

To add empty lines just add these:
```
title=-----------
``` 
That should do it...

(I havn't tested this, but if it doesn't work just open up an editor and comment out those lines)

---

