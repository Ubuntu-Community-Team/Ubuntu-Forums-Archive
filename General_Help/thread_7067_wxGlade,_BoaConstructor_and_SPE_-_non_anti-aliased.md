---
title: "wxGlade, BoaConstructor and SPE - non anti-aliased fonts?"
date: 2004-12-03
forum: General Help
---

### Post by stodge on 2004-12-03
I installed wxGlade, and also spe (Python GUI builder). I think they're both based on wxWidgets (wxPython). When I run them (and also Boa Constructor), it looks like they're using GTK1 and not GTK2 - the fonts are different to any other application running, and the fonts are not anti-aliased. Screenshots of these apps show them running with anti-aliased fonts, so it something wrong with my Ubuntu config?

Thanks

---

### Post by redrob on 2005-05-19
I'm seeing this on hoary.
It seems that libwxgtk 2.4 is compiled for gtk 1.2, not gtk 2.0.
You can see this by doing lsof, when an app that uses libwxgtk 2.4 is running,
or by doing a ldd on libwxgtk 2.4.

---

