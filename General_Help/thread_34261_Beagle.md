---
title: "Beagle"
date: 2005-05-14
forum: General Help
---

### Post by TheDude on 2005-05-14
Sorry if this has been covered already, but I've been having a problem with Beagle.  When trying to edit /etc/fstab, I get this;

edit /etc/fstab
Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

---

### Post by monchichi on 2005-05-14
[QUOTE=TheDude]Sorry if this has been covered already, but I've been having a problem with Beagle.  When trying to edit /etc/fstab, I get this;

edit /etc/fstab
Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"[/QUOTE]

don't use edit. it's not what you think it is. (if youre curious, run "man edit")
use gedit. or if your bent on using the console, try "vim" or the editor in "mc" is pretty great.

good luck...

---

### Post by Xian on 2005-05-14
[QUOTE=TheDude]edit /etc/fstab
Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"[/QUOTE]
Just change that command from a terminal to this:

$ sudo gedit /etc/fstab

---

