---
title: "TCL error"
date: 2018-08-18
forum: General Help
---

### Post by cmcanulty on 2018-08-18
I cannot open my chess program since upgrading to 18.04. The program is scidb. Here is the error I get

```
cmcanulty@Dell660s:~$ scidb-beta
Error in startup script: version conflict for package "Tcl": have 8.5.19, need 8.6-
    while executing
"package require Tcl 8.6-"
    (file "/usr/local/bin/scidb-beta" line 32854)
cmcanulty@Dell660s:~$
```

yet synaptic claims I have tcl 8.6 already installed. See screenshot below.

[ATTACH=CONFIG]280776[/ATTACH]

then I go further down the tcl search in synaptic and it shows tcl 8.5 and 8.6 installed, see second screenshot.  

[ATTACH=CONFIG]280777[/ATTACH]



What should I do to fix this? Thank you

---

### Post by &amp;KyT$0P# on 2018-08-18
I'm guessing you compiled [this source code]("http://scidb.sourceforge.net/download.html")?  If so, did you recompile after upgrading to 18.04?

---

### Post by cmcanulty on 2018-08-18
I installed it after the upgrade to 18.04. It works OK on another 18.04 computer. I downloaded a snapshot and did ./configure, make, etc. Would it be safe to completely uninstall the TCL version 8.5? It sounds like an important thing

---

### Post by Yellow Pasque on 2018-08-18
Try installing tcl8.6-dev and rebuilding (./configure, make).

EDIT: Also make sure tk8.6-dev is installed.

---

### Post by &amp;KyT$0P# on 2018-08-18
> **cmcanulty said:**
> Would it be safe to completely uninstall the TCL version 8.5? 
This is not necessary.  I tested building and running scidb on a 18.04 system with both versions of Tcl installed, and it seemed to work fine.

Did your 18.04 have all of the build dependencies installed when you compiled scidb?  From their [readme]("https://sourceforge.net/projects/scidb/files/") -
```
sudo apt-get install libexpat1-dev libfontconfig1-dev libfreetype6-dev libxft-dev libxcursor-dev tcl8.6 tcl8.6-dev tk8.6 tk8.6-dev zlib1g-dev
```

---

### Post by cmcanulty on 2018-08-19
Thanks, I had a;ready installed all the recommended apps but installing  tcl8.6-dev and then rebuilding worked, happy now!

---

