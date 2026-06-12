---
title: "openbox in unbuntu and menu.xml"
date: 2024-01-04
forum: General Help
---

### Post by faustf2 on 2024-01-04
hi  guys  i know ,is  possible in openbox in file menu.xml  insert icon  the  syntax  is icon="`/home/myuser/.local/share/icons/myfoto.png"  but  is  possible  insert a variable path ?   like /home/$(logname)/.local/share/icons/   (i tested this path but not  work )
thanks ? ?

---

### Post by MAFoElffen on 2024-01-04
No. 

You can insert Icons into the menu.xml, but you cannot use a variable path. The paths to things can be absolute or relative paths.

Although you can declare conditional if/then statements and variables within XML (xsl & xslt: extensible style sheet language), I do not think the OpenMenu logic that parses the menu.xml knows how to figure that out. There are no if, then or variables in the syntax of OpenMenu.org's menu.xml syntax.
RE: [http://openbox.org/wiki/Help:Menus](http://openbox.org/wiki/Help:Menus)

What are you trying to do or adapt to?

---

### Post by faustf2 on 2024-01-05
thanks  maybe  i will use  another place  like /usr/share/background/icons-app/, i want inser icon in menu of openbox  :D  thanks

---

