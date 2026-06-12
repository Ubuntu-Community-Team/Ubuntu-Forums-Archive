---
title: "video problems (blinky during games)"
date: 2008-05-17
forum: General Help
---

### Post by ricky_cullen on 2008-05-17
hi everyone,
i recently got my drivers working 
[http://ubuntuforums.org/showthread.php?t=777820]("http://ubuntuforums.org/showthread.php?t=777820")
and that worked for untill i tried running some games Wrazone 2100 works perfect but games like Frets on fire, Scorched 3D and Armagetron Advanced, run good FPS but seem blinky (best term i could think of) every couple of frams it blinks black.
i dont think it is my video card becasue these games ran good before.

thAnks for you help in advacnce

---

### Post by ibuclaw on 2008-05-17
Have you tried:
[LIST]
[*]A) Running the games with compiz disabled?
This command will do:
```
metacity --replace &
```
Then to get compiz back, switch the word "metacity" with "compiz"
[/LIST]
[LIST]
[*]B)  Running games in the FailSafe Terminal?
Choose to log into the "FailSafe Terminal" in the gdm startup screen, and type in "gnome-terminal" to open up a bigger terminal.
Then type in the name of your game to run it.
[/LIST]
Regards
Iain

---

### Post by ricky_cullen on 2008-05-17
worked perfectly thanks you very much

---

