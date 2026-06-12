---
title: "Printing problems in dapper 6.06"
date: 2006-10-09
forum: General Help
---

### Post by jphekman on 2006-10-09
Please let me know if this is the wrong forum for this thread, and if so, where to post it. Thanks!

I have an HP 6122 printer and am running Ubuntu 6.06. When I print using "lpr", the first three or so lines of every page are cut off. When I print from emacs using print-buffer, the page runs long, ie, one "page" of text takes up one page of paper plus a few lines of the next page. (Since the printer duplexes, this means you get a full page on one side and three lines only on the next side.)

I'm guessing I somehow have printing configured such that CUPS believes that my paper is longer than it actually is -- although printing from Firefox works just fine. Help?

Thanks! -Jessica

---

### Post by PaDV on 2006-11-13
Please give the output of the following command:
$ cat /etc/papersize

---

