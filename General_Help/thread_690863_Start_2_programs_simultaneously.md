---
title: "Start 2 programs simultaneously"
date: 2008-02-07
forum: General Help
---

### Post by holydhaliwal on 2008-02-07
Hey guys i was wondering if anyone could help me setup my system two have to programs start at the same time. For example i have a now playing screenlets installed and i want it set up so that when i start banshee THEN the now playing screenlets will start, and as well when i close banshee the now playing screenlet will stop. Any ideas? 

Thanks in advance.

---

### Post by pytheas22 on 2008-02-08
You could make a custom icon in gnome or in the panel and have it launch a script which would launch both your programs.  Make a script in your /home directory or somewhere, and just include the commands you need to launch the program from the command line.  And set up the icon to run that script when clicked.  Should be pretty simple.

If you don't know what the command to start a program is, you can figure it out by going into Prefernces>Main Menu, and finding the entry for the menu item of that program.  Then right click on it and select properties, and it will show the command that it uses to launch that program.

---

