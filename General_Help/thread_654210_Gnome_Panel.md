---
title: "Gnome Panel"
date: 2007-12-30
forum: General Help
---

### Post by sekinto on 2007-12-30
How do you remove the gnome panels?

---

### Post by jken146 on 2007-12-30
Right-click > Remove I think.  You can't remove the last one unfortunately, so resizing/autohiding/putting up with it will have to do.

---

### Post by dlegend on 2007-12-30
**To Remove All Panels**

1. Go to System > Sessions. Find the "Current Session" tab. 
2. Find gnome-panel and highlight it by clicking. For "Stye" change it to "Normal".
3. Close out of the Sessions manager. Now Press Alt + F2 and type:
> 
killall gnome-panel


The panels should be gone now.

In the future, you should only need to do step 3 when you log in to remove panels. If you want them permanently gone then let me know. You didn't really specify how you wanted removed (eg. permanent solution, just one panel, etc..)

---

### Post by jken146 on 2007-12-30
> **dlegend said:**
> **To Remove All Panels**

1. Go to System > Sessions. Find the "Current Session" tab. 
2. Find gnome-panel and highlight it by clicking. For "Stye" change it to "Normal".
3. Close out of the Sessions manager. Now Press Alt + F2 and type:

```
killall gnome-panel
```

The panels should be gone now.

In the future, you should only need to do step 3 when you log in to remove panels. If you want them permanently gone then let me know. You didn't really specify how you wanted removed (eg. permanent solution, just one panel, etc..)

Thanks for that.

---

### Post by sekinto on 2007-12-30
I would like them gone permanently, I could do your method and add 'killall gnome-panel' to my startup scripts. But is there a different method, one to stop them from starting up at all?

---

### Post by aktiwers on 2007-12-30
You could go to System => Preferences => Sessions
And under the "Current Session" tab remove "Gnome-Panel".

Then go to "Session Options" tab and click "Remember Currently Running Applications"..

Would that do the trick?

---

### Post by dlegend on 2007-12-31
> **aktiwers said:**
> You could go to System => Preferences => Sessions
And under the "Current Session" tab remove "Gnome-Panel".

Then go to "Session Options" tab and click "Remember Currently Running Applications"..

Would that do the trick?

That should work if you want a permanent solution for removing the gnome-panel. Probably best to log out and log back in before hand though so you don't have extra applications starting up when you log in.

---

