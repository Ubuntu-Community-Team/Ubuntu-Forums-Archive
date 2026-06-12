---
title: "Feisty, HPLIP and Python QT"
date: 2007-04-21
forum: General Help
---

### Post by ramjet_1953 on 2007-04-21
Hi, Guys!

I'm not sure how many people have come across this yet, but with a fresh install of Feisty, if you try to install HPLIP by using hp-setup, it tells you that PYQT is not installed.

It seems strange that an install detects that you have a HP printer, but does not automatically load-up the necessary Python QT libraries so that you can use hp-toolbox.

Must have been an oversight by the developers.

Regards,
Roger :cool:

---

### Post by JKyleOKC on 2007-09-02
I'm running into that exact problem, compounded by the fact that Synaptic does not appear to know of any PyQt package to install for me. Does anyone have a solution other than not using hp-toolbox?

EDIT: Found the solution in another thread a bit later: install python-qt3 which does have its listing in Synaptic. It worked nicely.

---

### Post by ramjet_1953 on 2007-09-03
[COLOR="Red"]sudo apt-get install python-qt3[/COLOR]

Regards,
Roger 8)

---

### Post by Steinar on 2008-05-28
> **ramjet_1953 said:**
> [COLOR="Red"]sudo apt-get install python-qt3[/COLOR]

Regards,
Roger 8)

Thank you Ramjet, that worked.  Now, can anyone tell me why python-qt4 didn't work?

I always choose the latest package, and when that didn't work I assumed a different package altogether was needed...

---

