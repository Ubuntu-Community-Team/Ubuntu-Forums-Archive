---
title: "block applications from using the &quot;system theme&quot;"
date: 2008-07-10
forum: General Help
---

### Post by b166er on 2008-07-10
Hi
Does anyone know of a method to block specific applications from using the color information used by the rest of the system?
I'm a big fan of dark themes, unfortunately some applications just don't work well with them. 
Sometimes they do white text on white backgrounds or black text on black backgrounds.
I've seen one that kinda blocks Firefox from using the wrong colors but is there something that I can use for more applications? Ideal would be something of a "blacklist".

---

### Post by b166er on 2008-07-17
ok i just found an alternate solution.
I found this litle command namned "sux"
with it i can run X applications using another user. So I won't load my gnome settings. although it's not a perfect solution obviously.
but I made a launcher out of it.

---

### Post by stchman on 2008-07-17
> **b166er said:**
> ok i just found an alternate solution.
I found this litle command namned "sux"
with it i can run X applications using another user. So I won't load my gnome settings. although it's not a perfect solution obviously.
but I made a launcher out of it.

I have been wondering about that myself.  I run the Ubuntu Studio theme and some apps don't behave well with the theme.

The only negative I can think is that when you do that the profile of the other person will be updated.

---

### Post by spupy on 2008-07-17
```
GTK2_RC_FILES=/home/uibxn/.themes/Aurora/gtk-2.0/gtkrc **gedit**
```

This will run gedit with the Aurora theme (as an example). All your themes in ~/.themes have a gtkrc file.
Locate the themes gtkrc and point to it like shown. You can easily modify your existing launchers. Also, you can use many different themes.

---

