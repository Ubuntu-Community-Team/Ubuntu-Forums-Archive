---
title: "using widets?"
date: 2007-10-21
forum: General Help
---

### Post by Tyke91 on 2007-10-21
i have enabled the widget layer in compiz fusion in gutsy, but i don't know where to get widgets or how to install them...

any help? i'd like a clock, a calculator, and maybe some games

---

### Post by Tyke91 on 2007-10-21
bump

---

### Post by Tyke91 on 2007-10-21
hmm... i made a spelling mistake in the name... oh well.


so far, i've found screenlets, but they dont seem to be working. I used ./configure make and make install to install them, but i also saw something about them only working on feisty/edgy  ... what do i do?

---

### Post by Tyke91 on 2007-10-21
alright, i now have my widgets installed, but how do i pipe them to the compiz fusions widget layer?

---

### Post by apple_and _linux on 2007-10-24
In the Compiz Fusion Widget settings, find the "Window Type" option and enter "type=Screenlets.py" (w/o the quotes.)  Let us know if it works.

---

### Post by vapore0n on 2007-10-24
screenlets work. Maybe you are not installing them correctly?

Start the screenlet manager (screenlets-manager) and then you can add to desktop.
Or you can run them directly :
$/home/zip-it/.screenlets/Calendar/CalendarScreenlet.py > /dev/null

---

