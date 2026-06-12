---
title: "[kubuntu] Krusader + xbindkeys mouse wheel dblclk jumps to top..?"
date: 2018-11-23
forum: General Help
---

### Post by dinkidonk on 2018-11-23
I have a fully updated Kubuntu 18.04.01 with xbindkeys/xautomation set up to perform a double click when I click the middle mouse button (mouse wheel). When I am using Krusader (Total Commander selection mode) and have a long list of files/directories (eg. /usr/share) and I scroll down the list and enter a directory and then leave the directory again the list i scrolled down to highlight the directory I just left. If I then use the scroll wheel (up or down), the list either jumps to the top or some pages upwards and that is quite annoying. If I instead of the middle mouse double click use an actual left button double click, this does not happen. Anyone who experiences the same issue, maybe knows a fix for this?

**~/.xbindkeysrc:**

```
"/usr/bin/xte 'mouseclick 1' 'mouseclick 1' &"
b:2 + Release
```

Thanks :)

---

