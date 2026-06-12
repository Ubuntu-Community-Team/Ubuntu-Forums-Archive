---
title: "problem with apache2 ubuntu 13.10's perl cgi"
date: 2014-01-27
forum: General Help
---

### Post by elim-qiu on 2014-01-27
Just installed apache2, php5 and mysql to my ubuntu 13.10, worked fine.

Installed basic texlive

then found  [http://localhost/cgi-bin/printenv.pl](http://localhost/cgi-bin/printenv.pl) not working!

The error msg is:  
Not Found
The requested URL /cgi-bin/printenv.pl was not found on this server

But I didn't do anything special with apache2 yet, and my ubuntu 12.04 perl cgi worked just fine.

The reason I mention texlive is that when I tried to uninstall apache and reinstall apache, it shows some files with texlive extra need to be removed too.

So my question is: Anyone have apache2 perl cgi worked out of box?  How can I fix the problem?

Thanks a lot.

---

### Post by elim-qiu on 2014-01-27
Well. I fixed the problem: need to enable mod_cgi.  In other words, The default apache installation forgot to add a **symlin** to cgi.load.

13.10 is good. But did add many bugs.

---

