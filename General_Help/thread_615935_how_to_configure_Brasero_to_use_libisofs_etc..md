---
title: "how to configure Brasero to use libisofs etc."
date: 2007-11-17
forum: General Help
---

### Post by raydar on 2007-11-17
I've had an unshakeable case of the can-burn-cds-but-not-dvds and thought I'd see whether an alternative to growisofs would help.  I saw that Brasero could be configured to do that, but surprisingly it lacks a preferences etc. menu item.  

The comment
[INDENT]Note: compiling against libburn is _not_enough. You need to activate the backend through GConf editor at "/apps/brasero/config/libburn_burn and /apps/brasero/config/libburn_iso"[/INDENT]
at [http://www.gnomefiles.org/app.php/Brasero](http://www.gnomefiles.org/app.php/Brasero) suggests that
1. I ought to have an /apps/brasero/config/ directory, but I don't have an apps folder in the root & can't find any apps folder that contains a brasero folder (brasero is installed), and
2. I have to recompile Brasero to use something other than growisofs--is that true, and is there an easier way to try libisofs?  

(For Xmas, how about a modest little config menu with that setting on it? :) )

---

