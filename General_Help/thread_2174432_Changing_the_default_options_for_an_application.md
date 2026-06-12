---
title: "Changing the default options for an application"
date: 2013-09-14
forum: General Help
---

### Post by pourranjbar_ar on 2013-09-14
Hi, 

I have just installed Texworks on my ubuntu. Now the application laucher successfully appears in the menu and whenever I click on a tex file, it opens up a Texwork editor. 

How can I make the texwork application always start with a set of specific options I have defined?

I have created a css file which controls the appearence of the textwork editor and I want textwork to follow my options whenever it opens up. 
At the moment, when I run textwork from the menu, the command "textwork" is executed. 
But I want it to exectue the following command 
**texworks -stylesheet ~/.TeXworks/configuration/mystyle.css **

I also want my options to be taken into account whenever I click on a tex file. In this case, the application opens up directly without me clicking on any menu items.

Any help is appreciated , 
thank,
ali.

---

### Post by CatKiller on 2013-09-15
I have no experience whatsoever with this particular program, but assuming you can generate a command line argument that loads the configuration you want to use, the definitions for launching an application are stored as .desktop files. You can probably find the one that starts your application and edit it accordingly.

---

### Post by scbingham on 2013-09-15
From within the Nautilus file manager, right click on a tex file, select Properties. Under the Open With tab, select the program you wish to use ie Texwork.

Use the same method for other file types too.

Hope that helps.

---

