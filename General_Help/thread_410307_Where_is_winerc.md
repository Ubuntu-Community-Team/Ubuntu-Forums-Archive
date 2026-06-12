---
title: "Where is winerc?"
date: 2007-04-15
forum: General Help
---

### Post by rocketman768 on 2007-04-15
So, I want wine to use my CUPS printer, but where is the winerc? I only have a ~/.wine directory.

---

### Post by JLB on 2007-04-15
not sure you still need it. that sounds like it is from 1999/2000 era wine.

gdi32.dll and winspool.drv should forward raw printer output to cups and/or lpr just fine. I have printing working under wine and have no such file (winerc)

However... wine should still respect a winerc located in your home directory

```
touch ~/.winerc
```
Edit it to suit your needs.

---

