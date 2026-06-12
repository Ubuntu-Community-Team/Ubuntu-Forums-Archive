---
title: "_gtk.so Python Errors on Only SOME Python Programs"
date: 2007-08-28
forum: General Help
---

### Post by moore.bryan on 2007-08-28
[I]okay, here goes:

when i run pypanel, no errors.  none.  nada.  when i run obmenu, this:
[/I]```
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so: 
undefined symbol: gtk_recent_action_get_type
```*please help... i've searched all over the forums and the net and found NOTHING.  i can't imagine i'm the only linux user in the world who's had this issue.*

---

### Post by hikaricore on 2007-09-28
Not just you.
Half of the python apps I have die with that.

Did you upgrade from Feisty?  I'm about to check launchpad to see if it's up there.

---

### Post by GregCwx1 on 2007-11-17
I've got the same problem with a clean install of Gusty (7.10). Funny thing is that some of these programs will run when fist logged in. After awhile though they stop. I've noticed this on add/remove programs and software sources apps when run from the menus. 

I just googled the problem and found ot might be related to

> /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so

not being found in the path. However, that doesn't explain why some apps will work and then stop working during the same session!

Argh!

---

