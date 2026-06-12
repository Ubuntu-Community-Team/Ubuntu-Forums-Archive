---
title: "laptop keyboard not work in gnome but does in kde, terminal, or failsafe gnome"
date: 2007-01-30
forum: General Help
---

### Post by harty83 on 2007-01-30
I have a compaq laptop and all of a sudden (for apparent reason at all) my keyboard has stopped working in gnome.  It works when logging in via gdm, it works under kde, and it works in failsafe gnome.  But as soon as I log into gnome, it completely stops functioning.  But as soon as I log out, it works fine.  Any idea what is going on?

Thanks!
Alan

Edit: Only keys that work are my bios function combination keys (fn-sleep, fn-brightness); no other key or combination of keys work.  But it works in every other OS so it is something with gnome specifically not the keyboard.  Help??

---

### Post by harty83 on 2007-01-30
Okay, so I'm one step closer.  I renamed the .gconf folder so that gnome will regenerate a default and my keyboard works now.  So what is it in the .gconf folder that would affect the keyboard?

---

### Post by harty83 on 2007-01-30
It was a problem in my .gconf/desktop folder.  I deleted the folder and all is well (which is a relief, I did not want to have to reset all my program defaults again!)  This seems to have also solved the problem where it takes a long time to send something to the trash.  

Thanks!
Alan

---

