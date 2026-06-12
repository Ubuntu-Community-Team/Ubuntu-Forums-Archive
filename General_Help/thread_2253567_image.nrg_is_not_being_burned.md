---
title: "image.nrg is not being burned"
date: 2014-11-20
forum: General Help
---

### Post by Robbyx on 2014-11-20
nrg2iso reported that the image.nrg is already an iso and so would not do a conversion.

I burned the image under brasero only to find that the image.nrg file was sitting on the DVD  with a checksum but none of the contents. I chose the burn option. 

Having used up my remaining DVD I am going to buy some more. In the meantime I have installed k3b. Should that burn it properly or is there a problem with burning an nrg recognised as an iso, that needs another solution?

---

### Post by bashiergui on 2014-11-22
Did you follow these instructions:[http://ubuntuhandbook.org/index.php/2013/09/one-command-to-convert-nrg-to-iso-in-ubuntu-linux/](http://ubuntuhandbook.org/index.php/2013/09/one-command-to-convert-nrg-to-iso-in-ubuntu-linux/)
```
nrg2iso image.nrg image.iso
```

---

### Post by Robbyx on 2014-11-22
Yes, I followed that article and the code. Instead of converting it, nrg2iso reported that it is already an iso, so there was nothing to convert. That error message did not help because when I came to burning the contents of the nrg file Brassero put the complete file on the disk without unwrapping the contents.

---

### Post by Habitual on 2014-11-24
> **Robbyx said:**
> nrg2iso reported that it is already an iso, so there was nothing to convert.Well then, how about
```
cp image.nrg image.iso
```
and burn that?

---

