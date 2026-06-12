---
title: "Cannot change settings, add icons to dock"
date: 2018-01-06
forum: General Help
---

### Post by greggorrell on 2018-01-06
Hey guys,

Fresh install of Ubuntu 17.10, I just came from the 16.03 LTS.  For some reason, I cannot make any changes to the dock.  If I try to add say the terminal to the dock, I will right click on it in the applications menu and select ad to favorites.  It will flash on the dock and disappear, and I'll see a notification that says it was added to favorites.  If I try to delete an icon from the dock, it will just come right back.  I also cannot change any settings either.  If I try to turn night light on, it just turns right back off when I let off the mouse.  Not all of the settings do it, it is very random..  I can turn global dark theme on and off, but right below it is on/off for Animations and I cannot change that.  Any idea what may be causing this?  I am even getting the same issues in the gnome-tweak-tool as well.

Thanks!

---

### Post by greggorrell on 2018-01-06
It  was a permissions issue..  anyone that keeps their home directory when  updating ubuntu or whatever in the future may run into this.  Try this  command with *user* being your username:
  sudo chown -r *user*:*user* /home/*user*

---

### Post by QIII on 2018-01-06
A caveat:  Although chown worked in this case, I would **not** use chmod recursively in /home/user.  Many of the files there are meant to have different permissions.  Changing them could result in a borked system. **So don't make that mistake**.

In any case, it's good to hear you sorted things out.  To make your solution easier for others to find, please mark this thread SOLVED by clicking on "Thread Tools" just above your first post and selection "Mark this thread as solved".

Cheers.

---

