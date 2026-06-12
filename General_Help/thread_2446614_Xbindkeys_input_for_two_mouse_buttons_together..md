---
title: "Xbindkeys input for two mouse buttons together."
date: 2020-07-03
forum: General Help
---

### Post by CaptainMark on 2020-07-03
I've an xbindkeys config file which currently switches to the next available workspace via sending the keyboard shortcut to xdotools, the mouse config is currently set to "b:10 + release" which is the side button on my mouse. 

This is good but I'd like to be able to have one for previous workspace as well so I thought that holding the side button "b10" and scroll down "b5" for next workspace or scroll up "b4" for previous workspace.

I've tried some different combinations but the closest I could get is using "b10 + b5" (or b4) but that has the opposite effect that I want in that the mouse wheel scrolls the workspaces *unless* the side button is being held too #-o

What combo should I put in my .xbindkeysrc to get this combo to work? I'm sure I'm just being silly but I can't figure it out. 

Regards
Mark

---

### Post by dragonfly41 on 2020-07-03
Does ctrl+alt+arrow (right arrow, left arrow) not work in toggling workspaces?

---

### Post by CaptainMark on 2020-07-04
Yeah, thats the command thats being passed to xdotools I'm trying to bind it to my mouse as well so I can quickly switch while still on the mouse.

---

### Post by dragonfly41 on 2020-07-04
I use Actiona quite a lot for workflow automation. It is in the repo.  I guess you could create two procedures which run Ctrl+Alt+Right and Ctrl+Alt+Left and then use a mouse event to call either of these procedures. Actiona is the GUI for developing and testing the script (which uses Qt objects and ECMAscript/Actionscript) and then you run the script (sans GUI) by running the **actexec myscript.ascr** command. Actiona has features similar to xdotool and in fact you can use Command object to run xdotool commands.  Or you might try Autokey.

---

