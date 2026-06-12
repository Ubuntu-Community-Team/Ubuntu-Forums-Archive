---
title: "Remove an item from the toolbar"
date: 2006-12-05
forum: General Help
---

### Post by Master Shake on 2006-12-05
My kids placed an item on the toolbar at the top of the screen.  When you click on it, it does nothing.  When you right click on it, it does nothing. I want to get rid of it, but it won't delete.  How can I get rid of it?

---

### Post by Titus A Duxass on 2006-12-05
Right click on the toolbar somewhere not on the button, it should give you an option to remove button or application.

(going from memory).

---

### Post by Master Shake on 2006-12-05
I only get that when I right click on an item on the toolbar other than the 'mystery app'

---

### Post by CatKiller on 2006-12-05
Does it have a handle nearby? (Normally a vertical line or box that people generally complain is too ugly and want to get rid of)

Failing that, you could open **gconf-editor** and try to identify which applet/object it is in /apps/panel and remove it, or failing **that** you could delete the ~/.gconf/apps/panel directory, which will give you the default panel setup again.

---

### Post by Master Shake on 2006-12-05
> **CatKiller said:**
>  or failing **that** you could delete the ~/.gconf/apps/panel directory, which will give you the default panel setup again.

That worked.  I didn't have much of anything other than the defaults on the panel anyway.

---

