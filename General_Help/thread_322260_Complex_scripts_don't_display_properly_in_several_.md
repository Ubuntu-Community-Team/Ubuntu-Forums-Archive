---
title: "Complex scripts don't display properly in several applications"
date: 2006-12-20
forum: General Help
---

### Post by zmr on 2006-12-20
I am trying to view Tibetan unicode script in Ubuntu Dapper. Tibetan is considered a complex script and thus needs special help to be displayed correctly. Gnome apparently has support for rendering complex scripts and indeed, Tibetan looks perfect in gedit and Evolution. In other programs like Abiword, OpenOffice, Opera, and Firefox (Firefox is fixable if you enable pango) Tibetan does not display correctly. I have tried enabling complex scripts in OpenOffice, but it had no effect on the display of Tibetan. Localizing  the locale settings in OpenOffice to Dzongkha (the Bhutanese version of Tibetan which is the exact same as standard Tibetan in terms of how it's rendered) and enabling support for Asian scripts also has no effect. Is anyone aware of solutions for getting complex scripts to display properly universally across different programs?

---

### Post by zmr on 2007-01-26
For OpenOffice it turns out that you need to have OOO 2.1 for Dzongkha/Tibetan script to display properly. As for Firefox, Abiword, and Opera, I am still investigating. Mozilla seems to be aware of the problem and may have a fix in Gecko 1.9 or perhaps sooner (does anyone have more info on this?) Tibetan rendering in Konqueror looks great.

---

