---
title: "cool fonts"
date: 2007-11-27
forum: General Help
---

### Post by mpgarate on 2007-11-27
is there a package with cool fonts? im putting together a logo and Im lookin around

---

### Post by Niniel on 2007-11-27
Sorry, can't help, but would like to know as well.
I tried out first AbiW then OO Writer for the first time the other day and was shocked at the fonts that came with Ubuntu. It's not that it's not a ton of them, but rather, that 80 % look identical. And some didn't even get displayed correctly (in OOW, the AbiW font preview is a total joke). Oh well. I'm sure I'll figure it all out eventually. :)

---

### Post by qqzhenyi on 2007-11-28
@Niniel : You might want to install the Microsoft font package
```
sudo apt-get install msttcorefonts
```
after install, type
```
sudo fc-cache -fv
```

@mpgarate : Check out some font sites like [http://www.dafont.com/](http://www.dafont.com/)
after you get the .ttf file(s), move them to /usr/share/fonts/truetype directory and type
```
sudo fc-cache -fv
```

---

