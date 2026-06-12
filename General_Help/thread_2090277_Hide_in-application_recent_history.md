---
title: "Hide in-application recent history?"
date: 2012-12-01
forum: General Help
---

### Post by abexman on 2012-12-01
I know there are ways via Privacy settings to control what recent activity is seen in the dashboard in 12.04 Ubuntu. Still many file viewing softwares and web browsers still show recent document history when opening those applications.  Is there any way to disable this or is there a good document viewer(s)  for text, pdfs, html, etc. files that does not save recent document history?

Thanks!

---

### Post by ohnonot on 2012-12-03
~/.local/share/recently-used.xbel 

either periodically delete this file or replace it with a 0-byte read only file to completely disable it.

might be different in unity though.

---

