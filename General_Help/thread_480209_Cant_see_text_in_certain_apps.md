---
title: "Cant see text in certain apps"
date: 2007-06-21
forum: General Help
---

### Post by rockyec78 on 2007-06-21
guys i m having a problem where i dont see text in certain applications, asample screenshot is attached
plz help me rectifying this problem

---

### Post by tvst on 2007-06-21
from the screenshot it seems yahoo messenger is a gtk1 application, so you may be able to solve it by editing your ~/.gtkrc file, like this:

style "user-font"
{
  font="-*-arial-medium-r-normal--24-*-*-*-*-*-iso8859-1"
}
widget_class "*" style "user-font"

i'm not sure if the font=... part is correct, so you may have to look it up online. it may also be that i'm wrong when i say yahoo messenger is a gtk1 application, in which case the .gtkrc file won't help.

---

### Post by energiya on 2007-06-21
rockyec78, using the official Yahoo package for linux is not an option theese days. It hasn't been updated for years. You would be better with Pidgin or GYache Improved.

---

