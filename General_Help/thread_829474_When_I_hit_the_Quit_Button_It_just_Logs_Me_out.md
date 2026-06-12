---
title: "When I hit the Quit Button It just Logs Me out"
date: 2008-06-14
forum: General Help
---

### Post by MORDOCtheGREAT on 2008-06-14
When I go to hit the "Quit..."  button it just loggs me out then I have to shut it down from the login screen.  Its kinda annoying.  Can any one help me.  Thanks.

---

### Post by Anduu on 2008-06-15
Open Applications->System Tools->Configuration Editor

Go to apps/gnome-session/options and make sure logout_prompt is checked.

---

### Post by MORDOCtheGREAT on 2008-06-15
Well...  I tried going Applications->System Tools->Configuration Editor and it doesn't seem to exist.  So I ran gconf-editor (I'm assuming its the same thing) and navigated my way to gnome-sessions-> options and the only thing I see there is "show_splash_screen" and "splash_image" but no log out prompt thing...  Also I don't know if this is related but I also can't change my theme.  Some of it I can but not all.  All I can modify is the controls and the pointer and nothing else....

---

### Post by MythosLegend on 2008-06-15
Try creating the key "logout_prompt" in /apps/gnome-session/options from gconf-editor. Make sure it is boolean type and the value is set to true.
If this doesn't work maybe your theme problem is related.  *shrugs*

---

### Post by MORDOCtheGREAT on 2008-06-15
Thanks MythosLegend that fixed it.  The last time I was updating my laptop just turned off and probably mussed somthing up. But no idea what the theme thing might be?

---

