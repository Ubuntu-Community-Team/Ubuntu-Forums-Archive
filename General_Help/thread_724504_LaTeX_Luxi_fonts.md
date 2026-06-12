---
title: "LaTeX Luxi fonts"
date: 2008-03-14
forum: General Help
---

### Post by rplantz on 2008-03-14
I have a LaTeX document that uses luximono fonts. I know how to install the font by hand, but I see that it is now in the repositories in the t1-xfree86-nonfree and ttf-xfree86-nonfree packages. I installed both packages and followed the directions to register them in /usr/share/doc/ttf-xfree86-nonfree/README.Debian, but they are not available.

Can anyone point me to documentation that tells how to make them available once these packages have been installed?

---

### Post by hugmenot on 2008-03-17
Tha classical way of making Type1 fonts available for use with TeX involves very awkward schemes. You certainly have to move the font file and the metrics into the texmf tree and tehn rename them according to the stupid Karl Berry naming scheme.

You would be better of to just use this ready-made folder:
[http://www.ctan.org/tex-archive/fonts/LuxiMono/](http://www.ctan.org/tex-archive/fonts/LuxiMono/)

---

