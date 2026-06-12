---
title: "font installation?"
date: 2008-05-05
forum: General Help
---

### Post by davidpbrown on 2008-05-05
I'm struggling to install new .ttf fonts.

The fonts are ttf chinese from [http://www.chinese-tools.com/resources/free-chinese-fonts.html](http://www.chinese-tools.com/resources/free-chinese-fonts.html)
for instance [&#28450;&#40718;&#32321;&#20013;&#35722; - HDZB_27.TTF]

I've found that 8.04 doesn't have fonts://

Instead, putting the fonts in ~/.fonts and then running 
```
sudo fc-cache -f -v
```
appears to have the system update its font library with these.

So, why don't these fonts now simply show up in OpenOffice etc?

---

### Post by sidrit on 2008-05-05
Try to place them in usr/share/fonts/truetype/ so they're available system-wide.
Then run the cache again.

---

### Post by davidpbrown on 2008-05-05
I tried that as well but makes no difference.

I put them in a folder there hdzb and got the same result fc-cache reports for others..

/usr/share/fonts/truetype/hdzb: caching, new cache contents: 10 fonts, 0 dirs

That the fonts are .ttf (and apparently would work in Windows) I was expecting they would install simply..

---

### Post by vishzilla on 2008-05-05
Log off and log back in. It should work. I have my extra fonts in ~/.fonts folder. I can use these in OpenOffice

---

### Post by davidpbrown on 2008-05-05
I tried that earlier too.

I've just posted to fontforge mailing list wondering the font is corrupt in some way.

Opening it and trying to regenerate the font into a clean .ttf throws some errors but then if it's valid for windows and isn't throwing any fc-cache errors, I'm expecting it is actually ok and this is just an installation issue?

---

