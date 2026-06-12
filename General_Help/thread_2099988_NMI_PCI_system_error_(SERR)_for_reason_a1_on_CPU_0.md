---
title: "NMI: PCI system error (SERR) for reason a1 on CPU 0."
date: 2012-12-31
forum: General Help
---

### Post by dfsg on 2012-12-31
Hi to all,

My computer (a lenovo thinkpad z61m 9450) running ubuntu 12.04.1 LTS randomly crashes. If it crashes it can do 3 things:

[LIST=1]
[*] the screen deforms in some kind of small stripes and, after +/- 2 sec, it becomes black
[*]the whole screen becomes some wird light blue collor
[*]parts of the screen disappear.
[/LIST]
In the log files i found 2 lines, written less than a second before my computer crashed:

```
NMI: PCI system error (SERR) for reason a1 on CPU 0. 
Dazed and confused, but trying to continue
```Does anybody have a solution for the problem?

Thanks in advance
 ~Dfsg

---

### Post by dfsg on 2013-01-05
anybody?

---

### Post by crau2 on 2013-01-31
Same issue.

---

### Post by tgalati4 on 2013-01-31
NMI is a non-maskable interrupt--which means it's an error that can't be categorized.  My guess is the graphics chip is delaminating causing the bus to freeze.

Do a google search on your model and see if others are having the same problem.  I know it is a problem with older thinkpads.

---

### Post by dfsg on 2013-02-19
I don't know how this can de a solution to anyone having the same issue but:

About a week ago my computer just froze, no wired screen effects, it just stopped responding, and i tried Alt+PrtSc+K and X restarted! After a few seconds of black it asked if i wanted to go in "low graphics mode", i clicked "yes" and ubuntu brought be back to the log-in screen.

That&#8217;s it. Since that moment i never had any problems with that error again! And not only that, some graphical errors where fixed to!

Before:
[IMG]http://img194.imageshack.us/img194/38/96921112.png[/IMG]

After:
[IMG]http://img571.imageshack.us/img571/6456/87472853.png[/IMG]

---

