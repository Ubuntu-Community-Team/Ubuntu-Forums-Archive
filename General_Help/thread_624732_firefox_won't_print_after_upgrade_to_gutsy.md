---
title: "firefox won't print after upgrade to gutsy"
date: 2007-11-27
forum: General Help
---

### Post by santana on 2007-11-27
Hi all after recent upgrade from fiesty to gutsy firefox does not print some web pages. When I choose print froom the file menu I get a message box that says:

XML Parsing Error: not well-formed
Location: chrome://global/content/printdialog.xul
Line Number 1, Column 1:
^

I guess this is a firefox bug. Anyone have experience with this?

---

### Post by NT4usB on 2007-11-27
A quick Google finds this:
```
You should close your Firefox and remove ~/.mozilla/firefox/*/XUL.mfasl and restart Firefox.
```
(fwiw, I'd move them instead of removing them... just in case you need to put them back *g*)
Found reference to this problem as far back as 2005. Not many solutions though.

---

### Post by zasf on 2007-12-02
I had the same problem, I didn't manage to solve it with removing files in ~/.mozilla, but a log out and log in fixed it!

---

