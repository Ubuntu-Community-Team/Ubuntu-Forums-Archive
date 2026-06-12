---
title: "why in Nautilus the folder doesn't open up when I drag files to the folders in the le"
date: 2018-08-05
forum: General Help
---

### Post by horizonbrave on 2018-08-05
Hi,
Ubuntu 18.04.1 here :)
when I drag files to the left pane in Nautilus I'm expecting that when I'm over that folder "bookmark" to spring-open up so that I could eventually place the file in a sub-folder... but it's not working!
Is it a design flaw of the drag'n'drop or am I missing something?
Sorry for a bad explanation, hope I've clear enough.

Many thanks

---

### Post by Claus7 on 2018-08-05
Hello,

if I understood correctly, drag and drop (dnd) behavior can be adjusted from dconf editor:
Applications->System tools->dconf Editor (in ubuntu 18.04 flashback)
under:
org/gnome/nautilus/preferences -> open folder on dnd hover: on

I was not able to find such an option for the left hand side pane though.

Regards!

---

