---
title: "can not change cursor in cursor selection"
date: 2007-12-01
forum: General Help
---

### Post by chunchengch on 2007-12-01
It is weird, I could change cursor in cursor selection (gcursor) before, but I can not change it now, even the "Install Theme" and "Go To Theme Folder" buttons do not work either.

I am not sure this problem is caused because of upgrading to 7.10, however, although I remove gcursor completely and then re-install it, the problem is still not solved.

Thanks for any help!

---

### Post by chunchengch on 2007-12-03
I saerch the web and still get no solution about this, need help!

Thanks!

---

### Post by jmehdi on 2007-12-16
Same problem as you.

(gcursor:7907): libglade-WARNING **: could not find signal handler
'extract_theme'.

(gcursor:7907): libglade-WARNING **: could not find signal handler
'open_theme_dir'.

(gcursor:7907): libglade-WARNING **: could not find signal handler
'entry_selected'.

(gcursor:7907): libglade-WARNING **: could not find signal handler
'size_changed'.

When I click on "Install Theme", "Go to theme folder" nothing happens ;
and I can't change the cursor theme.
:confused:

---

### Post by jmehdi on 2007-12-16
Just found the solution: no need of gcursor on Gutsy.

Just go to "System-Preferences-Appearance" then in the "Theme" tab click on
"customize" and in the "Pointer" tab select the cursor theme.

---

