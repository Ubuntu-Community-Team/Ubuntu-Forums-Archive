---
title: "how to clean up menu?"
date: 2005-04-26
forum: General Help
---

### Post by Digitallysick on 2005-04-26
Right now in my applications menu, under sound and video, are doubles of each icon, i try to use gnome menu edit (it doesn't show doubles) how can i remove the dup's from my menu??  *is new*

---

### Post by Professor X on 2005-04-26
```
rm -rf $HOME/.config/menus/applications.menu
```

and

```
killall gnome-panel
``` 

Cheers

---

### Post by DutchLau on 2005-04-26
Nice Proffessor X I've been waiting for this one to come for a while  :)  I never thought of asking because it's so pointless anyways (it's only aesthetics anyways- spelling?) Could you see if my little tutorial on the printing thing is right? 

Cheers mate,

---

### Post by Digitallysick on 2005-04-27
the code posted above did not do anything for me at all.  I still have menu dups

---

### Post by echris1 on 2008-05-31
killall gnome-panel worked for me.  I only had some menu items left over after I removed them with apt-get, but this cleared those out. Thanks!

---

