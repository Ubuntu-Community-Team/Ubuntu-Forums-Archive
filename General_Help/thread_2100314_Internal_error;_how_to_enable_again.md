---
title: "Internal error; how to enable again"
date: 2013-01-01
forum: General Help
---

### Post by Wim Sturkenboom on 2013-01-01
I regularly got this 'internal error' popup and eventually decided to choose the option to 'suppress further messages of this type'. Now I want to enable this message again. [COLOR="Blue"]How?[/COLOR]The apport functionality in /etc/default/apport is still enables, it's just for this specific error that it needs to be enable again.

Sorry, but I can't remember the exact wording.

As far as I can remember, the above error always refered to hplip/firmware.py (and yes, my printer no longer works).

---

### Post by dino99 on 2013-01-01
so your goal is to set your printer up.
if something is borked, then open synaptic to purge all the related hplip & cups installed packages, then reinstall cups & hplip (and their dependencies).

Then check if you can print (after a logout/in). If not, then you probably have some wrong settings inside either: .gconf, .gnome2, .local or .config (and can be deleted or renamed)
These folders are inside /home (ctrl+h to unhide them) and are automatically cleanly recreated on the next boot (but with the default settings, as its a reset, so your custom settings will be dropped indeed)

---

### Post by Wim Sturkenboom on 2013-01-01
Thanks for the reply.

Yes, the final intent is to get my printer going again. But this question was specific how to get the error message back.

Note:
I will keep your reply in mind for reference; I did a complete removal and installl of hplip already and that did not help.

PS
It's not likely that it's a problem in my home directory; an other user (own account) has the same problem.

---

### Post by Wim Sturkenboom on 2013-01-05
Time for a kick :)

---

