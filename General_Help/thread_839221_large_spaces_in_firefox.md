---
title: "large spaces in firefox"
date: 2008-06-24
forum: General Help
---

### Post by GStubbs43 on 2008-06-24
Hey guys...

I'm not sure how this happened, becuase it seemed to be all of a sudden, really.

In Firefox 3, there are large spaces between every word, in site text, text inputs, and the UI.

It's only Firefox 3, I installed Fx2, and it's normal.

I also tried uninstalling/reinstalling a few times, deleting ~/.mozilla, and installing Fx3 from the Mozilla website, the problem won't go away.

It's probably an easy fix, but can you guys help me?

---

### Post by wasimo on 2008-07-14
Hi GStubbs43,
 
It seems that you have the same problem as I have.  I've posted this problem on lauchpad.net, the bug number is 247129.  Have you already found a solution to the problem ? If not, then please read my post.  As you can see there, I have already taken some steps to find the cause of the problem and to resolve it eventually.  The next thing to do, would be to replace the contents of the /usr/lib/xulrunner-1.9, /etc/gre.d and /etc/xulrunner-1.9 folders with a new version, but I haven't come to that yet.

                   wasimo

---

### Post by wasimo on 2008-07-14
Hi again, GStubbs43,

The problem is solved.  Please look at bug number 247129 in launchpad.net.  It seemed that this bug was already reported earlier in the year.  Closing Firefox and any xulrunner-1.9 applications and then doing a complete remove of pango-graphite should solve the problem, as JM Williams of launchpad.net pointed out.

---

