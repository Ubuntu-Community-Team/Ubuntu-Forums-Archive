---
title: "GTK theme not changing properly"
date: 2008-05-09
forum: General Help
---

### Post by Separ on 2008-05-09
As the title says, my GTK theme is not changing from my last one properly. Screenshot below.

---

### Post by macaholic on 2008-05-09
I'm sorry, I fail to see what isn't changing, could you be mroe specific as to what isn't changing?

---

### Post by Exsecrabilus on 2008-05-09
Are you using Emerald Theme Manager alongside that?

---

### Post by macaholic on 2008-05-09
> **Exsecrabilus said:**
> Are you using Emerald Theme Manager alongside that?
Is that what he is talking about? The window borders not changing? In that case, you are right, emerald is drawing window decorations.
If you want the other window decorations, just run ```
gtk-window-decorator --replace
```

---

### Post by Separ on 2008-05-09
Look at my top menu bars (applications etc), it is meant to be all black/shiny but it still has white from my previous gtk theme.

---

### Post by macaholic on 2008-05-09
Does killing the gnome panel do anything?
```
killall gnome-panel
```
It should restart right away.

---

### Post by Separ on 2008-05-09
Restarted panel but didn't fix it =\

---

### Post by macaholic on 2008-05-09
Hmph, well that is a perculiar problem, will it change for any other theme?

---

### Post by Separ on 2008-05-09
Nope, no themes work properly.

---

### Post by Separ on 2008-05-09
AHA! I fixed it. The panel background was set to a solid colour, not to use the system theme.

Thanks anyway tho.

---

