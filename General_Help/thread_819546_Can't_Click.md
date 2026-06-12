---
title: "Can't Click"
date: 2008-06-05
forum: General Help
---

### Post by amtur_poet on 2008-06-05
I accidentally overwrote the function of Button 1 in the compiz effects menu, and now I can't click on anything. What should I do?

---

### Post by sisco311 on 2008-06-05
Open a terminal. 
Alt+F2 and type: ***gnome-terminal*** and hit Enter
edit your config file:
```
gedit ~/.config/compiz/compizconfig/Default.ini
```search for a line like:
> some_text_here **=** **Button1**and delete it. 

Save the file(Ctrl+s) and your done.

---

