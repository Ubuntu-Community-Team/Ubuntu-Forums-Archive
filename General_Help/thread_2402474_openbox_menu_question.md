---
title: "openbox menu question"
date: 2018-09-30
forum: General Help
---

### Post by babag on 2018-09-30
just starting out trying to edit my openbox menus. in the default menu setup, 'applications' is in the root menu as a pipemenu that seems to be calling obamenu. under the 'applications' category there are more submenus: office, development, graphics, internet, etc.  how do i move these submenus to the root and get rid of the 'applications' category? i'm using obmenu.

thanks,
babag

---

### Post by Holger_Gehrke on 2018-09-30
I do believe a look at the manual page of obamenu will give you a good idea on how to solve this. obamenu is a python script that takes neither a configuration file nor command line options but is configured by making changes in a configuration section at the beginning of the script.

Holger

---

### Post by babag on 2018-09-30
thanks, holger. i'll give that a look. 

g

---

### Post by babag on 2018-09-30
well, i looked that over but couldn't figure anything out. can't figure out whether it's something to edit in obamen, menu.xml, or if it's possible to do it from obmenu. love the configurability but i'm not a programmer, just a user who want to move the categories up a level. usually would be a drag/drop thing i guess but not in openbox. i guess this case is due to the pipemenu nature of the section. makes things hard for me to decipher.

thanks,
babag

---

