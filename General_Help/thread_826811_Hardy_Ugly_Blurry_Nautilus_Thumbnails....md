---
title: "Hardy Ugly Blurry Nautilus Thumbnails..."
date: 2008-06-12
forum: General Help
---

### Post by 6205 on 2008-06-12
**[COLOR="Sienna"]If you are frustrated by ugly, blurred Nautilus thumbnails in Ubuntu Hardy, you gonna need this...[/COLOR]**

---

### Post by skymera on 2008-06-12
Thank you, I've never had problems with thumbnails though.

---

### Post by Kilz on 2008-06-12
I had this problem, small graphics were blown up and looked ugly. In case someone else finds this and needs directions.

1. Open a terminal type in  gconf-editor and hit enter.
2. Look under apps > nautilus > icon view
3. Right click on Thubmnail_size and choose Edit Key
4. Change 96 to zero
5. enter the following command ```
rm -f ~/.thumbnails/normal/*
```
6. Close all open nautilus windows and open them again.

---

### Post by NilsE on 2008-06-12
If you also use nautilus in root mode you will have to do the same thing with

gksudo gconf-editor

Root and user have separate profiles

---

### Post by Kynan on 2008-06-30
Thankyou so much for posting this, it's been bothering me for quite some time especially when i edit icon themes browsing the smaller icons like 16x16 just looks downright ugly, why on earth did ubuntu change this?

---

### Post by NilsE on 2009-05-25
This option broke somewhere between Hardy and Jaunty and a "0" size now displays no thumbnails.  

Does anyone know a workaround for this other than setting just a smaller than 96 icon size to get variable size icons again.

---

### Post by 6205 on 2009-07-08
> **NilsE said:**
> This option broke somewhere between Hardy and Jaunty and a "0" size now displays no thumbnails.  

Does anyone know a workaround for this other than setting just a smaller than 96 icon size to get variable size icons again.

Yeah, currently you cannot set up '0' propably due code changes in GNOME :( 
However at least i have changed it from 96 to 32 in both my and root profiles..

---

