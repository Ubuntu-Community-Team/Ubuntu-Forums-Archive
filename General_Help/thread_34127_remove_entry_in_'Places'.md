---
title: "remove entry in 'Places'"
date: 2005-05-13
forum: General Help
---

### Post by JulesH on 2005-05-13
Hi,

As a total newbie, I inadvertantly put an entry in the 'Places' drop down menu, which shows up in nautilus etc, as well. I don't remember how I put it there!

I installed smeg, but this won't remove entries in 'Places'. Is there a way to manually get rid of entries?

How do I do it?

jules

---

### Post by JulesH on 2005-05-13
[QUOTE=JulesH]Hi,

As a total newbie, I inadvertantly put an entry in the 'Places' drop down menu, which shows up in nautilus etc, as well. I don't remember how I put it there!

I installed smeg, but this won't remove entries in 'Places'. Is there a way to manually get rid of entries?

How do I do it?

jules[/QUOTE]

Don't worry, I managed to sort it myself. If you delete the folder the entry refers to, then do a:

killall gnome-panel 

in a terminal window, then it dissappears!

Jules

---

### Post by Alexander Kirillov on 2005-05-13
[QUOTE=JulesH]Don't worry, I managed to sort it myself. If you delete the folder the entry refers to, then do a:

killall gnome-panel 

in a terminal window, then it dissappears!

Jules[/QUOTE]
The "right way" to do it is as follows. Open file selector dialog form any app - for example, start gedit, click on "Open". In file selecor dialog, left pane contains the same items as places menu. Select the item you do not want, then click "remove".

---

### Post by JulesH on 2005-05-13
[QUOTE=Alexander Kirillov]The "right way" to do it is as follows. Open file selector dialog form any app - for example, start gedit, click on "Open". In file selecor dialog, left pane contains the same items as places menu. Select the item you do not want, then click "remove".[/QUOTE]


Thanks, I'll make a note of that. I'm sure I will do it again sometime.

Jules

---

