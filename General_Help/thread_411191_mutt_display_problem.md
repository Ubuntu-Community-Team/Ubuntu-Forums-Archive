---
title: "mutt display problem"
date: 2007-04-16
forum: General Help
---

### Post by agrewal on 2007-04-16
Hi Everyone,

I just installed xubuntu fiesty. I am facing a problem with the display of mutt. In the threaded view, instead of arrows I get some wierd junk characters. What could be the problem?

I installed mutt by manually compiling and applying the side bar patch. It was compiled against the libncurses5-dev package. I am thinking this might be a terminfo issue, but I have no idea what exactly it is.

BTW, I tried it in a bunch of different terminals, xterm, rxvt etc. I get the same junk everywhere.  I have pasted the problem below, if it helps
[FONT="Courier New"]
||r  | bappa                     | Participation Status                               | Wed, 07 Mar 2007 10:59:20 +0530 |  3.2K |
||  F| To bappa                  | &#65533;T~T&#65533;T~@>                                                 | Wed, 07 Mar 2007 11:37:18 +0530 |  1.2K |
[/FONT]

I would appreciate any help with this problem.

Regards,
Ajeet.

---

### Post by agrewal on 2007-04-18
For the record,

I fixed it. Seems that you need to compile it with libncursesw-dev instead of libcurses-dev. 

Regards,
Ajeet

---

### Post by andrew.46 on 2007-08-04
Hi,

 Saw your mutt solution:

> **agrewal said:**
> For the record,

I fixed it. Seems that you need to compile it with libncursesw-dev instead of libcurses-dev. 

Regards,
Ajeet

 and thought hmmmmm...... libncurses5-dev???

                 Andrew

---

