---
title: "System&gt;Preferences&gt;startup missing"
date: 2008-06-10
forum: General Help
---

### Post by thered on 2008-06-10
I seem to be missing my 'startup programs' from the preferences list.  Any ideas on how to get it back - or a terminal command to run the GUI

---

### Post by kostkon on 2008-06-10
Actually, it's called *Sessions* not *Startup Programs*.

Right click on your menu, select *Edit Menus* and check if it is unselected. In that case, just enable it again and it will appear in your *Preferences* menu.

If it does not exist at all, then create a new entry and give *gnome-sessions-properties* as its command.

---

### Post by thered on 2008-06-10
doh! Thank you sir. :)

---

### Post by abuzzbuzz on 2009-03-30
Can anyone help me here.  I accidently dragged my sessions option to firefox, and now it is not there.  If I try to add it back to the menu, I get :  Failed to execute child process "gnome-sessions-properties" (No such file or directory)

If I try to type gnome-sessions-properties from a command prompt, it states command not found.

Thanks.

---

### Post by |Porsche on 2009-03-30
Follow post #2.

---

### Post by abuzzbuzz on 2009-03-30
If I do that, I get:
I get : Failed to execute child process "gnome-sessions-properties" (No such file or directory)

Thanks

---

### Post by |Porsche on 2009-03-30
Seems like you might need to reinstall gnome-session.

---

### Post by abuzzbuzz on 2009-03-30
I tried to reinstall gnome-session and gnome-session-caberra
Same
I tried to uninstall completely those two items, then install.
Same

Any other suggestions?

---

### Post by kanikilu on 2009-03-30
Isn't it *gnome-session-properties* rather than *gnome-session**s**-properties*?

---

### Post by abuzzbuzz on 2009-03-31
Your right, that's what I have been trying,  I just mistyped it here.
Still can't get it to work.

---

