---
title: "Top panel icons moving out of place everytime I log in..."
date: 2008-05-07
forum: General Help
---

### Post by Moonfrost on 2008-05-07
I don't know, but I think Hardy is not perfect at all...in fact, it seems to be worse than Gutsy...why? every time I start the computer the icons on the top panel at very right side are all out of place...sometimes the thrash can icon changes itself from the right (where it's supposed to be on the bottom panel) more to the left and the workspaces move more to the left...but now the icon has disappeared and I have no idea how to access the thrash can, can anybody tell me please? and does anybody know why all these things happen? I don't want to have to move everything every time I start.

I have found out though that that only happens when I login to my normal account and not when I log in as root...is there a way to make the trash can icon appear again?

---

### Post by drs305 on 2008-05-07
You can lock the icons in place in the top panel by right clicking the icon and selecting 'move' to put it where you want and then 'Lock to Panel' so it doesn't move. Note: you may not be able to move an icon past one that is locked, so you may have to unlock some of the icons first.

You can add the trash icon to the top panel by right clicking an empty spot on the panel and selecting "Add to Panel". In the options is a "Trash" option.

---

### Post by Moonfrost on 2008-05-07
> **drs305 said:**
> You can lock the icons in place in the top panel by right clicking the icon and selecting 'move' to put it where you want and then 'Lock to Panel' so it doesn't move. Note: you may not be able to move an icon past one that is locked, so you may have to unlock some of the icons first.

You can add the trash icon to the top panel by right clicking an empty spot on the panel and selecting "Add to Panel". In the options is a "Trash" option.

They were already locked to panel, and I tried adding a new thrash can icon and nothing happened...it didn't appear at all.

---

### Post by drs305 on 2008-05-07
To get the trash can on your desktop, you could try running the following command:

```
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible 'true'
```

As for the panel problems, you might try reinstalling gnome-panel via synaptic.

---

### Post by Moonfrost on 2008-05-07
> **drs305 said:**
> To get the trash can on your desktop, you could try running the following command:

```
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible 'true'
```

As for the panel problems, you might try reinstalling gnome-panel via synaptic.

Thanks...I logged out and back in the the thrash can icon was there no problem...I restarted to check on something else and the icon disappeared again, so I logged out and logged back in once again and there it was again...I don't get it. Haven't had anymore panel problems so far again but if I do I will try re-installing and see what happens...thanks.

---

