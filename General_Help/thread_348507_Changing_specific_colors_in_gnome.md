---
title: "Changing specific colors in gnome?"
date: 2007-01-28
forum: General Help
---

### Post by ardchoille42 on 2007-01-28
I am using gnome on Ubuntu 6.06.1 LTS (Dapper Drake) and I love it. The Ubuntu devs did an outstanding job on Dapper :)

I would, however, like to change the color of the panel text without changing the color of anything else. Or changing the color of the titlebar text without changing the color of anything else. I know this is possible because there is an app called gnome-color-chooser which does this. I tried to compile this app and got a bunch of missing deps for gtkmm-2.4, libglademm-2.4 and libxml2. I looked in the Dapper repos and saw some -dev packages but those want to install 30 or so other packages and I don't want to pollute my system in the case that those dev packages weren't what I needed.

Someone mentioned that all it takes to change the color of the panel text is to put some code into ~/.gtkrc-2.0 and logout and back in for the changes to take effect. This seems easier than trying to compile an app and guessing the deps I need.

What I would like to know is the proper syntax for that code in ~/.gtkrc-2.0 and what exactly I can and cannot change with that method.

Is there a listing of what I can and cannot change by manually editing ~/.gtkrc-2.0 and the syntax used to make those changes? Does someone have a working example of this?

Thank you :)

---

