---
title: "Startup settings severely messed up"
date: 2006-10-20
forum: General Help
---

### Post by PathSpace on 2006-10-20
My gnome panel NEVER starts up when I first log in to my computer any more.  :( 

I always must hit ctrl-alt-backspace and try logging in again to get the gnome panel.  Sometimes when I do this, Beryl won't start, but that's not too bad since Beryl does start sometimes (and I can always start Beryl manually).

I am running a fully updated Edgy system.

Can anyone help me?

---

### Post by invalid on 2006-10-20
Try adding 'gnome-panel &' into your session start-up programs, or simply typing it in a terminal after you begin your session.

---

### Post by PathSpace on 2006-10-20
I've tried issuing the command gnome-panel, but it says that a panel is already running (even though there is not one).

---

### Post by invalid on 2006-10-22
try
```
killall gnome-panel && gnome-panel &
```

---

