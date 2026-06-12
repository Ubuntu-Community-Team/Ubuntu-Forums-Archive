---
title: "TeX problem"
date: 2017-01-20
forum: General Help
---

### Post by hmiersch on 2017-01-20
hi. under 14.04 i created a TeX document that uses the glossaries package, and that worked as it should. then i switched to 16.04 and installed texstudio again. when i tried to compile my old document, texstudio gave me an error saying it couldn't find glossaries.sty. so i read the readme and followed the instructions. then it complained that it couldn't find etoolbox.sty. so again i followed the installation istructions, but that didn't do me any good, it still complains that it can't find etoolbox.sty. so here's my question: where is etoolbox.sty supposed to be? or how can I tell texstudio where to look for it?

---

### Post by steeldriver on 2017-01-20
It seems to be part of the texlive-latex-extra package - did you install that?

---

### Post by hmiersch on 2017-01-20
no, unless it comes with texstudio. but considering texstudio cant find etoolbox, i guess it doesnt.

---

