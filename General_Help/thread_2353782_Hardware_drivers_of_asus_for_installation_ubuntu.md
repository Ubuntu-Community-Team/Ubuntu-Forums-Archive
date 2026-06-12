---
title: "Hardware drivers of asus for installation ubuntu"
date: 2017-02-24
forum: General Help
---

### Post by wr3x on 2017-02-24
i got a brand-new asus laptop with windos10 and bunch of driver softwares but i need to install gnome ubuntu on it before that i want to know will it affect to drivers softwares and afters installation wil my wifi graphic work as same as before?

---

### Post by wildmanne39 on 2017-02-24
Run gnome ubuntu in the try before you install mode and see how it works then post the output of the following commands in the terminal by hitting CTRL+ALT+T:
```
lspci | grep VGA
```
it will tell us the graphics card you have then run:
```
lspci -nnk | grep -iA2 net
```
for the wifi card.
Thanks

---

### Post by gordintoronto on 2017-02-25
With brand new hardware, I suggest "brand new software." Which would be 16.10 or 17.04, if Ubuntu Gnome has a beta version.

---

