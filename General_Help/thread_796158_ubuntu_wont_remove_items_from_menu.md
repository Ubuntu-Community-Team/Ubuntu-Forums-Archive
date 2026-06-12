---
title: "ubuntu wont remove items from menu"
date: 2008-05-16
forum: General Help
---

### Post by nzadLithium on 2008-05-16
Hey 

I'm using the ubuntu menu editor. (right click menu go edit menu).
I think the program is called alacarte?

When i click on items in the menu editor and click delete it doesn't remove the menu item. I'm trying to clear it out because there is like 100 entries in the 'other' category. If i tell it not to show them it doesn't show them but i would still like to delete them as i feel its taking a longer time to display gnome-panels icons etc on start up than it did when i originally installed ubuntu. I feel this is probably contributing to the time its taking. (It still takes alot less time than win xp though :p ).

Thx for any suggestions

---

### Post by ibuclaw on 2008-05-16
Press "**Alt+F2**" and type into the Run Application bar:
```
nautilus ~/.local/share/applications
```
Remove any unwanted apps from there.

If there are any directories in the "Others" subdirectory contents, then go up a level and enter the "desktop-directories" folder.
Or just press "**Alt+F2**" again and type:
```
nautilus ~/.local/share/desktop-directories
```

Regards
Iain

---

### Post by nzadLithium on 2008-05-16
thx for the reply. I tried what you said. Half the things in the 'other' submenu weren't in there but i removed the ones that were. They still showed up in alacarte so i told to delete. I still had the nautilus window of that directory open. As soon as i told to delete it added two of the ones i told it to delete into that folder. When i closed alacarte it seems to have removed one of each duplicate from inside the folder (so there is only one of the item in there again). It has had no effect in alacarte as to deleting the items.
I'm going to bed now but i'll be sure to check for any suggestions in the morning.

---

