---
title: "Panel Shadows in Compiz"
date: 2007-03-09
forum: General Help
---

### Post by happy-and-lost on 2007-03-09
I love the fact that Feisty comes with Compiz, and is really nicely preconfigured, but I do not like the shadows it puts on the gnome panels I have (see shot)!

It's a very n00bish question, but is there a way to disable panel shadowing?

---

### Post by BKonkle on 2007-07-08
I actually just discovered the answer to this today.  In the Window Decorations plugin settings, under the Effects heading, change the "Shadow Windows" section to "any & !(class=Gnome-panel)".  This works perfectly for me in Compiz Fusion to remove the shadow from the gnome-panel, but it still keeps it everywhere else.

---

### Post by doctorgreg on 2007-11-28
Thanks this worked like a treat!!!

---

### Post by Hibountu on 2007-11-30
If you use 

```
any& !(type=dock) 
```

instead, you keep shadows under the menus, but still get rid of them under the 
panel.

---

### Post by montechristos on 2008-04-10
If i want to remove shadows from the windows to?

---

### Post by vhex on 2008-04-15
montechristos, just disable the shadow plugin?

---

