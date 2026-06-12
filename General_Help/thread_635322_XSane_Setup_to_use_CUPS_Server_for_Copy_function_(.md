---
title: "XSane Setup to use CUPS Server for Copy function (HowTo)"
date: 2007-12-08
forum: General Help
---

### Post by LarryJ2 on 2007-12-08
I couldn't find what needed to be inserted into the XSane Image Scanner setup dialog to make the Copy button work.   Here's how I got it working. I am using Kubuntu GutsyGibbon 7.10. and KDE 3.5.8.

First of all, excellent documentation is available by hitting F1  or   Help -> XSane Doc.  Thank you Oliver Rauch!

In Preferences, Setup, Copy,   I changed "new printer"  to "Default"   and "lpr"  to  "kprinter --stdin --nodialog -P Lexmark4039-10R"  since I am using KDE and my default cups printer is named Lexmark4039-10R.   Then I clicked Apply  and OK.


LarryJ

---

