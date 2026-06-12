---
title: "emerald not taking over"
date: 2008-06-25
forum: General Help
---

### Post by dexter.deepak on 2008-06-25
i thought simply installing emerald would make it the default window manager..but it isnt.
i think "emerald --replace" should do it .. but i am afraid of trying this command...bcoz i dont know how to revert to my current manager in case of an error.

---

### Post by Sub101 on 2008-06-25
I think ```
compiz --replace
``` should return you to your current setup.

---

### Post by Het Irv on 2008-06-25
No, to make emerald the defualt you need to add a session Under "System -> Prefrences -> Sessions"  use emerald --replace as the command.  If for some reason emerald doesn't work, open a terminal and type "metacity --replace" to use the default manager.

You shouldn't have any problems using emerald --replace though.

---

### Post by Enlitend on 2008-06-25
IIRC , it's not necessary to put it on startup sessions.

Once emerald is installed, launch and import theme, select theme to use. ALT-F2, type in "emerald --replace". ( that should kick in the window decoration effects )

Go into CCSM -> Effects -> Window Decoration -> Command 
and type in " emerald --replace " press Enter. That will do the trick.

---

