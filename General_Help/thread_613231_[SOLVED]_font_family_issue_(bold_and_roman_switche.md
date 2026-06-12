---
title: "[SOLVED] font family issue (bold and roman switched?)"
date: 2007-11-14
forum: General Help
---

### Post by omicist on 2007-11-14
Hi all,

I have an odd issue with certain true-type fonts in Linux, including the Windows Vista fonts (Corbel, Calibri, Cambria, etc.) and the Delicious free font.  I have a script that I wrote to install these fonts as follows:

```

#!/bin/bash

for f in $@
do
        echo $f
        cp $f ~/.fonts/ttf
done
cd ~/.fonts/ttf
ttmkfdir > fonts.scale
mkfontdir
xset fp rehash
```

This works great for every other font that I've tried; however, although gfontview shows both the regular and bold families in my .fonts/ttf directory, Firefox and Epiphany only use the bold variant of the Vista fonts, and XeTeX switches the bold and regular variants for Delicious.  Anyone else have this problem, know where it originates, or have an idea of how to fix it?

Thanks a lot.

---

### Post by omicist on 2007-11-15
Whoops, I'm an idiot.  This was actually two separate problems:

1) One of the Vista fonts is named .TTC or something instead of .TTF, so my wildcard didn't pick it up.  Whoops!

2) I was having a problem with "Delicious" in XeTeX.  I think this is because the font name is "Delicious-Regular.otf" for the regular weight variant, but the name of the actual font within the family is "Delicious-Roman".  So the moral of the story is, if you're using any extra fonts in XeTeX and you get weirdness, open the font with fontforge and make sure you're calling it correctly :)

---

