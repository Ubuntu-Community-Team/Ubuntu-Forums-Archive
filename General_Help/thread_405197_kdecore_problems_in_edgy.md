---
title: "kdecore problems in edgy"
date: 2007-04-09
forum: General Help
---

### Post by os.getlogin on 2007-04-09
hey all.

I keep getting errors when issuing KDE execs from the command line in Ubuntu:
% klipper                                                                                                              
klipper: symbol lookup error: /usr/lib/libkdecore.so.4: undefined symbol: qt_x_user_time

or

kile                                                                                                                   
kile: symbol lookup error: /usr/lib/libkdecore.so.4: undefined symbol: qt_x_user_time

But these run fine if I select them from the applications menus.

Any ideas?

Nate

---

### Post by os.getlogin on 2007-04-09
solved.

There was apparently a problem with a path in my environment variable $LD_LIBRARY_PATH.  I cleared it and all is good.

Nate

---

