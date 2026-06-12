---
title: "Printing PDF file: Scale to fit page problem"
date: 2005-10-22
forum: General Help
---

### Post by RudiRoss on 2005-10-22
I am trying to Print a pdf page that is smaller than the paper size, but I just don't get the driver to scale it to fit the page properly.

I am using an HP LaserJet 1200 and tried both the pxlmono and the PostScript driver, with the following command:

lp -o media=A4 -o fittopage -o fitplot myfile.pdf

and

lp -o media=A4 -o scaling=200 myfile.pdf

But the size of the printed page did not change with either of the commands.

Any pointers whats going wrong appreciated.

TIA,

Rudi

---

