---
title: "disabled delete in gnome-keybinding"
date: 2006-09-08
forum: General Help
---

### Post by Sqwishy on 2006-09-08
in gnome-keybinding-propertys where you change all the shortcuts i was trying to disable one but i didnt read at the bottom to press backspace and assumed it was delete ... so i pressed delete and assigned delete to the perticular action. then i disabled it after a few atemps but now my delete key isn't binded to anything ... please help? is there a bind command? ](*,)

---

### Post by croak77 on 2006-09-09
Well, you can try looking in your /home/username folder. There should be a hidden folder (Ctrl-h in Nautilus will show/hide hidden items) called .gconf, .gconf2, and/or .gconfd. you can try deleting those but they might delete all your personal settings for any GNOME app that uses gconf.

---

