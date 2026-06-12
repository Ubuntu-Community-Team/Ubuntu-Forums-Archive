---
title: "Accidentally deleted ~/Desktop"
date: 2008-01-28
forum: General Help
---

### Post by ajmedfor on 2008-01-28
I somehow managed to accidentally delete ~/Desktop, then when I rebooted it made my home folder become my desktop. I re-created the ~/Desktop file, but it is still linked to my home folder. I don't need the desktop files back, I just want to re-link my desktop to the correct folder. Can anyone help?

---

### Post by erfahren on 2008-01-28
open up the gnome configuration editor - in terminal just do
```

gconf-editor

```
I don't recall everything exactly - but somewhere like Apps > Nautilus there's an option to "Make desktop the home folder" - uncheck it and recheck it. You might have to log out and back in between the checking it to get it to take (just mess with it in other words).

that should do it hopefully.

---

### Post by erfahren on 2008-01-28
hey, I remembered another thread about this earlier but didn't have it bookmarked - I went to look for it but got distracted for awhile

anyway, it gives better information then what I gave before - so if you didn't get it fixed with my (questionable) instructions earler here it is :[Stuff from my home directory appears unwanted as icons on my desktop](http://ubuntuforums.org/showthread.php?t=609005)

note: to put a link to the gnome configuration editor in your menu just open up "alacate" (the menu editor) - System > Preferences > Main Menu - and the selection for it is under Applications > System Tools

---

