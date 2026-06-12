---
title: "Links open in wrong browser"
date: 2007-05-05
forum: General Help
---

### Post by CocoAUS on 2007-05-05
I've changed my preferred web browser to Epiphany and also changed the HTML filetype association to Epiphany.  However, links in e-mails (in Evolution, no less) still open in Firefox.  WTF?

---

### Post by Dekunuts on 2007-05-05
Yup, i've seen that happening too and i don't know why. Some applications respect your settings and others don't. It's not a big deal, but I too would like an answer.

---

### Post by CocoAUS on 2007-05-11
I found the answer.

In gconf-editor, go to /desktop/gnome/url-handlers/ and change the value in there.  Works like a charm.

---

