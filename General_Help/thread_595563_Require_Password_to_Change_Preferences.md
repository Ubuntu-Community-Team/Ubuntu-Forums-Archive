---
title: "Require Password to Change Preferences"
date: 2007-10-28
forum: General Help
---

### Post by Jeffrey903 on 2007-10-28
My friends keep trying to mess with me by enabling VNC on my computer without a password (by System -> Preferences -> Remote Desktop), and then randomly move the mouse when I'm on my computer.  So I then go and disable remote desktop, but if I step out of the room for a moment, they will just enable it again (since it only takes a few clicks).  I usually try to remember to lock the machine, but I don't always do it.

I was looking for a way to require a password before changing any preferences (especially the remote desktop ones), but can't find it.  I couldn't imagine that it's not possible, but I just can't find it.  Can anyone help me out?

Thanks,
Jeff

---

### Post by strabes on 2007-10-28
A bad fix but you could remove the "Remote Desktop" option from the preferences menu by going to System > Preferences > Main Menu and then unchecking or deleting that menu item.

---

### Post by daengbo on 2007-10-29
Your roommates sound like sharp cookies (jerks, too ...). Type the following in a terminal:
 sudo chmod go-x /usr/bin/vino-preferences
This will keep the preferences for remote desktop from running. If you ever need to enable remote desktop, type the following first:
 sudo chmod go+x /usr/bin/vino-preferences

Best of luck with those guys!

---

