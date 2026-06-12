---
title: "cannot access bash_profile or bashrc"
date: 2007-12-17
forum: General Help
---

### Post by Jazzua on 2007-12-17
I'm sure this is probably my fault and i've done something really stupid and obvious but i can't seem to access my bash profile. i type:

edit /home/jazz/bash_profile

and i get this error message

Warning: unknown mime-type for "/home/jazz/bash_profile" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

I've just switched from windows and am trying to get my stuff for java development up and running. I need to access bash_profile (so i've read) to insert path variables for the java sdk. apart from not really being comfortable with the terminal yet my experience of ubuntu has been one of sweet relief. so much faster and easier and just plain lighter on my system (especially since i came from vista). Any help with this problem though would be really, really appreciated.

---

### Post by geirha on 2007-12-17
it's .bash_profile, note the dot (.). The dot infront makes the file hidden. Instead of edit, try gedit. ```
gedit ~/.bash_profile
```

You can also access this file from nautilus (the file explorer), but since it's hidden you have to tell it to show hidden files. Hitting Ctrl+h will toggle that.

---

### Post by Jazzua on 2007-12-17
thanks heaps geirha, that worked perfectly.

---

