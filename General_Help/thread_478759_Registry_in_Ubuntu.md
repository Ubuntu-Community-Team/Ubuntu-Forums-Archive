---
title: "Registry in Ubuntu"
date: 2007-06-19
forum: General Help
---

### Post by tL0z on 2007-06-19
I've always heard that Linux hasn't a registry like Windows and, therefore, it's more safer and efficient than Windows.  So, where does Linux keep the information regarding the system and the programs? In individual configuration files?
By the way, Gconf is one of those files, right?

---

### Post by rattking on 2007-06-19
linux keeps system and default settings as text files  in /etc 
user settings are kept in the users /home directory and start with a .
files that start with a . are hidden by file managers unless show all files is selected
ls -a
in the command line shows all files as well
then you can view  them with any text editor
be carefull editing things in /etc and remember to make a backup copy before modifying 

I don't know exactly how or were gconf keeps its settings.. havent used gnome much

---

