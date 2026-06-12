---
title: "can't build gtk+ applications"
date: 2007-05-12
forum: General Help
---

### Post by elfprince13 on 2007-05-12
hello everyone.

I'm running Ubuntu 7.04 andI have installed build-essentials package, gtk+2.10.0 and its development package, but whenever I try to build a gtk+ application I get an error similar to the following:



> In file included from /usr/include/gtk-2.0/gtk/gtkwidget.h:32, 
from /usr/include/gtk-2.0/gtk/gtkcontainer.h:33, 
from /usr/include/gtk-2.0/gtk/gtkbin.h:32, 
from /usr/include/gtk-2.0/gtk/gtkwindow.h:33, 
from /usr/include/gtk-2.0/gtk/gtkdialog.h:32, 
from /usr/include/gtk-2.0/gtk/gtkaboutdialog.h:28, 
from /usr/include/gtk-2.0/gtk/gtk.h:32, 
from asmide.c:23: 
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: expected specifier-qualifier-list before &#8216;GInitiallyUnowned&#8217; 
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: expected specifier-qualifier-list before &#8216;GInitiallyUnownedClass

this is really getting to be a pita, since I need to build several applications that don't have .debs. any help would be appreciated.

---

### Post by elfprince13 on 2007-05-16
has ANYONE seen this before? when I googled it I found 2 results, none of which had solutions, and one of which was in german.....

---

### Post by elfprince13 on 2007-05-24
please help someone? this really is rather urgent, and one of the few things preventing me from switching to Ubuntu entirely.

---

