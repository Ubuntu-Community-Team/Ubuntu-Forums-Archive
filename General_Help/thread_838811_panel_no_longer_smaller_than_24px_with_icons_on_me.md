---
title: "panel no longer smaller than 24px with icons on menus"
date: 2008-06-23
forum: General Help
---

### Post by tedrampart on 2008-06-23
I just recently upgraded to hardy (last night actually), and while most things have been worked out, I have run into a very annoying issue.

_**before upgrading**_, I had the top-panel size set to 19px, and it was using the ubuntustudio iconset.

**_after upgrading_**, the lowest I can go is 24px with the icons in the menus.. if I turn the icons off in the menus, it goes back down to 19px, add the menu icons, back to 24px.

I've searched all over for a fix on this, everything I found said to edit the icons to make them smaller.  so I found smaller icons, and it just scaled them up to 24px.

I don't get why it worked great in gutsy, and now its not working at all (with any icon theme).  and it makes a big impact on screen realestate with my 13" 1280x800 screen.

---

### Post by easybake on 2008-06-24
Panel size is also limited to the font size you set. If you go into the System>Preferences>Appearance under the font tab and change the application font to something smaller like size 6. You should then be able to decrease the bar size. It will scale down the icons.

---

### Post by tedrampart on 2008-06-24
yea my font is already at 8, and it seems unproportionally smaller next to the big 24px icon in the menu.  

like I said, it gets smaller if I choose not to show icons in menus, the rest of the icons on the panel scale, it just seems to be the one on the menu bar thats causing this issue.

---

### Post by easybake on 2008-06-24
Apparently, after checking, the system only forces the icon to be 24 or larger. I would suggest just removing it from the panel and adding the Main Menu applet in its place. For some reason that has no problem scaling down.

---

### Post by tedrampart on 2008-06-24
yea, I noticed that with "gimmie" applet (which I was going to use as a replacement since I use it on my eeepc, but its still too buggy for my work machine)..

I'll use this, but I'm going to keep searching for a fix, starting to look like a menu bar issue.. maybe gconf-editor has a setting for it

thanks for the suggestion mate..

---

