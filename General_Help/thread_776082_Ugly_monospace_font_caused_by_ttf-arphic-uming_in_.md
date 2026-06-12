---
title: "Ugly monospace font caused by ttf-arphic-uming in Ubuntu 8.04"
date: 2008-04-30
forum: General Help
---

### Post by tarjxvf on 2008-04-30
I installed Ubuntu 8.04 LTS, the only thing that I was not satisfied is that the fonts in the terminal, acroread etc. were very ugly (I believe they are all monospace fonts). 

I found that the ugly monospace fonts came from the package ttf-arphic-uming. So my workaround is to uninstall this package:
```

$ sudo apt-get remove --purge ttf-arphic-uming

```

However, I think this is not the ideal way to do it, as some people do need this font (it's a Chinese font). So my question is, is there any way to avoid using the font ttf-arphic-uming as a monospace font (in the terminal, acroread etc.) without uninstalling it?

Thanks!

P.S.
My environment: LC_CTYPE=zh_TW.UTF-8

---

