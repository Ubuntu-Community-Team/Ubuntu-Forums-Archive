---
title: "GTK3 incorrect colours behind Menu bar"
date: 2013-06-05
forum: General Help
---

### Post by jman6495 on 2013-06-05
Hey guys

I have got my system set up quite nicely, on gnome from PPA, Version 3.8

Thing is for some reason the menubars (File Edit etc ... ) have a background instead of being transparent,
 the result is this :
[IMG]http://i.imgur.com/YmqTqvL.png[/IMG]

Does anyone have any idea how to get rid of this ? I just want it to blend in to the rest of the theme !

 Thanks for any help

           Jman6495

EDIT : 
So i partially fixed it, it's now just dropdown menus that are horrible

I added 
.menuitem {
background-color:#2d2d2d;
}
to the code, background-color being the dark colour missing in the screenshot

This causes trouble with menus though

---

