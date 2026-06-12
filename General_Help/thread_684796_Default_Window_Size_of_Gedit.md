---
title: "Default Window Size of Gedit"
date: 2008-02-01
forum: General Help
---

### Post by fjgaude on 2008-02-01
Anyone know how to change the default size of the Gedit window when it comes up?

---

### Post by ayoli on 2008-02-01
I don't think there is an option to do that, actually I've resized mine then closed it and now when I launch it it comes up at the last size.

edit another way : edit this file in your home
```
vi ~/.gnome2/gedit-2 
```
You should have something like this with (wow) height and width properties :)
```
[window]
width=854
height=776
state=0
side_panel_active_page=1907370066
bottom_panel_size=130
bottom_panel_active_page=-1116604772
```

---

### Post by fjgaude on 2008-02-01
Thanks, I'll give it a go. I see the file and have changed the sizes... will see what happens when I re-boot.

---

