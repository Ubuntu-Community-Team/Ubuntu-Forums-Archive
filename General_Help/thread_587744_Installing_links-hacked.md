---
title: "Installing links-hacked"
date: 2007-10-23
forum: General Help
---

### Post by JMO707 on 2007-10-23
I will be brief.

I want to use [links]("http://links.twibright.com/") in graphical mode, but miss just the tabs. The only other console-based browser apart from it capable of do that that I have found is [links-hacked]("http://xray.sai.msu.ru/~karpov/links-hacked/"), but I can't seem to be able to compile it.
I'm having troubles with the freetype fonts like the ones mentioned [here]("http://www.stud.fh-dortmund.de/~jkorte/links/install-links-hacked.html#possibleerrors") (I think), but really don't understand how to solve them. Eitherway, it would be nice to find a deb package of it (I haven't)

Anyone uses it or can help me?

---

### Post by 23meg on 2007-10-23
What errors are you getting when trying to compile?

---

### Post by JMO707 on 2007-10-23
This are the final lines of make:

```
font.c:8: error: la declaración static de ‘prune_font_cache’ a continuación de una no static
links.h:1534: error: la declaración previa de ‘prune_font_cache’ estaba aquí
make[2]: *** [font.o] Error 1
make[2]: se sale del directorio `/home/jmo/Desktop/links-hacked'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/jmo/Desktop/links-hacked'
make: *** [all] Error 2
```

---

### Post by JMO707 on 2007-10-23
Bump!

---

### Post by zikki on 2008-04-30
[http://zikki-majestic.livejournal.com/40716.html](http://zikki-majestic.livejournal.com/40716.html)

---

