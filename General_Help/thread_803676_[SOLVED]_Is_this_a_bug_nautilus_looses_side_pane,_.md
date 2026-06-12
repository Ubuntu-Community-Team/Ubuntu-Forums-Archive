---
title: "[SOLVED] Is this a bug? nautilus looses side pane, toolbars"
date: 2008-05-22
forum: General Help
---

### Post by fsando on 2008-05-22
Now this is really strange. Nautilus just lost the side pane, the toolbars and the address bar and I see absolutely no way getting them back.

What happened???
The items in the 'view' menu are fewer than normal and does NOT contain the option "Side Pane F9"

Clicking a folder opens a new instance of nautilus with the same deficiencies.

So how to get the "old nautilus" back?

Turns out the solution is to right click on a folder and choose "open in a new window"

---

### Post by jeannacav on 2009-11-25
> **fsando said:**
> Now this is really strange. Nautilus just lost the side pane, the toolbars and the address bar and I see absolutely no way getting them back.


...


Turns out the solution is to right click on a folder and choose "open in a new window"

That last post was spring of 2008.

This has happened to me now.
I no longer can just open my home folder and get the usual screen.
I must right click a folder then choose to browse it.
Then my user folder shows up with my name and this home folder is its parent.
I never saw this looking this way before and I want a one (not 4) click entry back, please.
(f9 is not even there)

(I probably clicked or right clicked something not meaning to?

thanks for any help.

jeanna

---

### Post by raktarok on 2009-11-26
When you start nautilus like this, you should get the normal window.
```
nautilus --browser
```
To fix this permanently, open nautilus and go to Edit > Preferences >  Behavior. (Or just do 'nautilus-file-management-properties' from a terminal/Run dialog) 
Then tick mark the 'Always open in Browser windows' entry.
If this does not solve the problem, I don't know what is wrong...

---

### Post by jeannacav on 2009-11-26
Thank you raktarok,
The tick 'always open in browser window' worked.
I am glad it was simple, and I 

THANK YOU,

jeanna

---

