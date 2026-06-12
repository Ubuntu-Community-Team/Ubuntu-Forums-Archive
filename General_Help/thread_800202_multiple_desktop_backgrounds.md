---
title: "multiple desktop backgrounds"
date: 2008-05-19
forum: General Help
---

### Post by dazift on 2008-05-19
i am using compiz fusion and i set up a 4 sided cube and i was wondering how to make each one have its own background if that is possible. i tryed playing with the appearance settings in ccsm, under: desktop cube,appearance, background images. i put in four of them with no change. 
i am sorta new to this and would appreciate any help thanks.

---

### Post by Genius314 on 2008-05-19
Open a terminal or press Alt+F2, and type gconf-editor.
Then go to /apps/metacity/preferences and uncheck the "show_desktop" option.
Unfortunately this also disables desktop icons, but of course you can always use a dock. :)
(If you still want desktop icons, you'd have to recompile nautilus from source with some changed code. I can't help with that, and you probably shouldn't if you don't know what you're doing.)

EDIT: Oh, yeah, you have to log out and back in (or restart X, ctrl+alt+backspace. Be sure to save and exit everything first!!) to see the changes.

---

### Post by dazift on 2008-05-19
alt+f2
gconf-editor

i get back: the command failed to run

---

### Post by dazift on 2008-05-19
oh ok i got it
i right clicked the desktop and unchecked "let x4wm4 manage desktop" and i got the wallpapers that i picked with ccsm
thanks anyway!

---

### Post by nefarion_the_engineer on 2009-11-11
> **dazift said:**
> oh ok i got it
i right clicked the desktop and unchecked "let x4wm4 manage desktop" and i got the wallpapers that i picked with ccsm
thanks anyway!

Im running ubuntu 9.10. I chose 4 backgrounds in ccsm. But this last part "right click desktop" doesnt make sense to me... what desktop? a button? the actual desktop? I cannot find the place to uncheck "let x4wm4 manage desktop". Please tell me how you did this.
Thanks

---

