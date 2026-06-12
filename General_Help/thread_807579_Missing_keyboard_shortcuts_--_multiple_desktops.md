---
title: "Missing keyboard shortcuts -- multiple desktops"
date: 2008-05-25
forum: General Help
---

### Post by casperlingus on 2008-05-25
Recently did a fresh install of Hardy (had Gutsy before).  I typically set up my box with 4 desktops, and map the F9-F12 keys to move between them, and Shift-F9-12 keys to move windows between them.  

The default desktop count is 2, so I increase it to 4 and then go to System->Preferences->Keyboard Shortcuts to do the key mappings.

It appears in Hardy, even after a reboot, that there are no options beyond desktops 1 and 2.  There is no keyboard options for desktops 3 and 4.  In the past, once those other desktops are added (at least after a reboot) those options show up in that shortcuts dialog.  In fact, I can't even think of a workaround to handle the other two desktops.

This is a crucial problem.  My entire life is typically organized on 4 desktops and being able to switch between them quickly.  Help...?

-Casper

---

### Post by casperlingus on 2008-05-25
Just found the solution to this with a bit of gconf-editor searching.

Well, that's precisely the solution:  in a terminal type 
```
gconf-editor
```

Then follow the path: 
```
apps -> metacity -> global_keybindings
```

and from there you can set the keys appropriately.  There's a lot of good stuff in gconf-editor, but sometimes it can be tough to navigate.

-Casper

---

