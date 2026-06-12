---
title: "Evince crashes with dvi files"
date: 2007-01-11
forum: General Help
---

### Post by Nonno Bassotto on 2007-01-11
Yesterday Evince started not being able to open dvi files. Sometimes it just fails, other times it opens them with wrong fonts, then crashes after a while.

It seems that there is a problem with font creation or with permissions. The output of
```

evince anyfile.dvi

```
is
```

kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 1+0/600 --dpi 600 cmtt8
mkdir: impossibile creare la directory `././var/cache/fonts': Permesso negato
mktexpk: mktexdir /var/cache/fonts/pk/ljfour/public/cm failed.
kpathsea: Appending font creation commands to missfont.log.
page: Warning: font `cmtt8' at 600x600 not found, trying `cmr10' instead
page: Warning: cmtt8: checksum mismatch (expected 3745761907, got 1274110073)
kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 1+0/600 --dpi 600 cmbx8

```
and so on.

"impossibile creare la directory" means "impossible to create the directory" and "Permesso negato" means "Permissions denied".

I'm able to see dvi files with xdvi, and with the correct font, but without antialiasing (I don't believe that the two problems are related.

I should mention that this happened after I installed TeXlive in place of TeTeX. I tried going back to TeTeX, thinking that it was a bug of the xdvi bundled with TeXlive. The situation was identical, so I turned back to TeXlive and nothing changed again. I also tried to switch to the package evince-gtk, and then switch back, with no results.

Any help would be appreciated (even a line saying "I happily use TeXlive and dvi visualization works").

Thank you

---

