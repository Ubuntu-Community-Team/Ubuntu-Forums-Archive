---
title: "how to end xtightvncviewer session?"
date: 2006-07-04
forum: General Help
---

### Post by monkman on 2006-07-04
hi.

i'm connecting from a kubuntu pc to a xubuntu one. i established a vnc connection. on the kubuntu side xtightvncviewer is what i'm using. how do i disconnect from the viewer side proper? 
now i'm using ctrl+alt+esc and then one mouseklick. ist that ok?

THANK YOU!

---

### Post by scxtt on 2006-07-04
shouldn't matter much how you get out of it, it'd probably be more important that you make sure the server connection is killed once you do ... i don't use xtight* but after i "close" a vnc connection (either by clicking the close button or a logout) i just do a "ps -ef | grep vnc" and kill the server ... that way i don't have :1, :2, :3, etc. connections running after i'm done w/ them ...

---

