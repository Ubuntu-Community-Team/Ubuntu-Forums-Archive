---
title: "How do you delete icons?"
date: 2018-09-23
forum: General Help
---

### Post by shiningkenmonster on 2018-09-23
Tried for googling it. Can't find a solution! Lots of google searches show outdated stuff. How do I remove the file icon on the left? I have two! I can't right click on the button and remove as favorites.

Also, how do i remove 0ad icon on the activities apps?

[IMG]https://preview.ibb.co/b4LQSU/Screenshot_from_2018_09_22_22_56_15.png[/IMG]

---

### Post by vanadium on 2018-09-23
These icons are created from .desktop files present systemwide in your /usr/share/applications folder and these in your home folder under .local/share/applications. On your system, there will be a redundant .desktop file somewhere that is creating the second item. You will need to locate the redundant .desktop file and delete it.

---

