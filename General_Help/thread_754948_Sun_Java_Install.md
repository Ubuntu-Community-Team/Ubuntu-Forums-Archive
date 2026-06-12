---
title: "Sun Java Install"
date: 2008-04-14
forum: General Help
---

### Post by CarollaTony on 2008-04-14
I am trying to load the java runtime from Sun, to resolve a compatibility issue I am having with some java apps, and I need some help.  I have downloaded the rpm, and when I install it, here is what I see:

```
error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0_05-fcs.i586
        /bin/cat is needed by jre-1.6.0_05-fcs.i586
        /bin/cp is needed by jre-1.6.0_05-fcs.i586
        /bin/gawk is needed by jre-1.6.0_05-fcs.i586
        /bin/grep is needed by jre-1.6.0_05-fcs.i586
        /bin/ln is needed by jre-1.6.0_05-fcs.i586
        /bin/ls is needed by jre-1.6.0_05-fcs.i586
        /bin/mkdir is needed by jre-1.6.0_05-fcs.i586
        /bin/mv is needed by jre-1.6.0_05-fcs.i586
        /bin/pwd is needed by jre-1.6.0_05-fcs.i586
        /bin/rm is needed by jre-1.6.0_05-fcs.i586
        /bin/sed is needed by jre-1.6.0_05-fcs.i586
        /bin/sort is needed by jre-1.6.0_05-fcs.i586
        /bin/touch is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/find is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0_05-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0_05-fcs.i586
        /bin/sh is needed by jre-1.6.0_05-fcs.i586
 
Done.

```

All of the listed files exist in the folders they are listed in.  Is there something I am missing?  I am not sure where to look--is there an install log when using rpm?  Any help would be greatly appreciated.  Thanks!

---

### Post by ibutho on 2008-04-14
Ubuntu does not use rpms by default. You can install Sun Java from the Ubuntu repos. Take a look at this [article]("https://help.ubuntu.com/community/Java") for detailed instructions.

---

