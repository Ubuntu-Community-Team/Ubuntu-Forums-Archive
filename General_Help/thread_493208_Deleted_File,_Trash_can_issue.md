---
title: "Deleted File, Trash can issue"
date: 2007-07-05
forum: General Help
---

### Post by MrBungle821 on 2007-07-05
Well, there is a protected file inside my Trashcan, but yeah, IT WONT DELETE!, I looked inside my .trash folder, and it's empty, but the Trashcan on the bar thingy still has a file in it. Please help me, what can I do?

---

### Post by Qu4k3R on 2007-07-05
open the gnome-terminal or the konsole.
Do this:

> 
cd ~/.Trash
sudo rm -r *


This will remove everything you have on your trash folder.

---

### Post by MrBungle821 on 2007-07-05
It still doens't work! :(

[IMG]http://s7.photobucket.com/albums/y283/mrbungle821/?action=view&current=Doesntwork.png[/IMG]

---

### Post by MrBungle821 on 2007-07-05
ugh, double post, but see link for information, or whatever.

[http://s7.photobucket.com/albums/y283/mrbungle821/?action=view&current=Doesntwork.png](http://s7.photobucket.com/albums/y283/mrbungle821/?action=view&current=Doesntwork.png)

---

### Post by MrBungle821 on 2007-07-05
Anyone? :(

---

### Post by MrBungle821 on 2007-07-06
Umm, anyone? Please help!

---

### Post by Catsworth on 2007-07-06
Please post the result of:

```

cd ~/.Trash
ls -a

```

---

