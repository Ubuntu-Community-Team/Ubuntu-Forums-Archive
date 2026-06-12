---
title: "AMSN install Help"
date: 2007-09-25
forum: General Help
---

### Post by kolslorr on 2007-09-25
HI, 

I do not know if this is the correct place, but here goes...

Got this error on instaling AMSN in GUTSY, complaining abt some TCL stuff... I installed all those likely TCL stuffs in synaptics but nothing works..

ANynoe?

---

### Post by useResa on 2007-09-25
I installed the packages **tcl8.4** and **tcltls** and this solved the issue for me.
```
0 rdrijsen@rdrijsen-gutsy: ~
Tue Sep 25, 15:42 $ sudo apt-cache policy tcl8.4
tcl8.4:
  Installed: 8.4.15-1
  Candidate: 8.4.15-1
  Version table:
 *** 8.4.15-1 0
        500 http://nl.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
0 rdrijsen@rdrijsen-gutsy: ~
Tue Sep 25, 15:43 $ sudo apt-cache policy tcltls
tcltls:
  Installed: 1.5.0.dfsg-6
  Candidate: 1.5.0.dfsg-6
  Version table:
 *** 1.5.0.dfsg-6 0
        500 http://nl.archive.ubuntu.com gutsy/universe Packages
        100 /var/lib/dpkg/status
```

You can install these packages through Synaptics or by using a terminal
```
sudo aptitude install tcl8.4 tcltls
```
Please note that for tcltls you need to have the Universe repository activated.

---

### Post by kolslorr on 2007-09-25
Thanks for your help! i got it installed finally through Add/Remove Program... turn out that the AMSN package installer was crap... :)

Another question, why did the AMSN window looks so ugly in Gutsy now? It looked fine in my old Feisty before... What am I missing this time again?

:):)

---

### Post by useResa on 2007-09-25
I have the same ... so can not help you on this.
I was able to improve the looks slightly by opening the Preferences (Account --> Preferences) and then in the Appearance tab click the "Change font" button (using Trebuchet now instead of the default font Helvetica.

---

