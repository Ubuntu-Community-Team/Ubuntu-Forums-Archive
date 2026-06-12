---
title: "How to get file name printed by kprinter ?"
date: 2008-06-16
forum: General Help
---

### Post by romain31 on 2008-06-16
Hi all,

When I use kprinter, I print toto.txt for exemple, it creates a temporary file and lauches the command lpr with this temporary file:
/usr/bin/lpr -P 'couleur_SD_bac_manuel' '-#1' '/tmp/kde-rlopez/kprinter_11493'

I would like to be able to get the filename toto.txt, in order to use it later on a print filter. The spooler only see the temporary filename.
There is maybe a solution to make the original filename appears in the command line.

Thanks in advance for any suggestion

Romain

---

