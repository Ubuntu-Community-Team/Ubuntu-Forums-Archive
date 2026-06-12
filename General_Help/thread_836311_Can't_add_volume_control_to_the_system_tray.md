---
title: "Can't add volume control to the system tray"
date: 2008-06-21
forum: General Help
---

### Post by Borsook on 2008-06-21
Hi, it worked perfectly in 7.10, but after installing 8.04 (clean install) I can't add it there, i.e. just nothing happens. Sound works fine, I can add all other "applets" (not sure how to call them. If anyone has an idea what's causing this I'd be grateful.

---

### Post by x1a4 on 2008-06-21
Hi, and welcome to the forums. 

Do you use other panel plugins that use the progress-bar, like Free Space Checker, System Load etc?  Do they work?

I've had the same problem and it turns out that the GTK theme was to blame.  When I changed the theme the plugins changed with it, but when I restarted the panel (like when logging-in for instance) all the plugins which use the progress-bar were gone and I was unable to add them or any other.  When I changed the theme again, everything worked.  Try changing themes and see if it works.

EDIT: you shouldn't add the volume control to the system tray, but to the panel.  The system tray is a panel plugin which doesn't allow other plugins inside it.

---

### Post by Borsook on 2008-06-21
> **x1a4 said:**
> Hi, and welcome to the forums. 

Do you use other panel plugins that use the progress-bar, like Free Space Checker, System Load etc?  Do they work?

I've had the same problem and it turns out that the GTK theme was to blame.  When I changed the theme the plugins changed with it, but when I restarted the panel (like when logging-in for instance) all the plugins which use the progress-bar were gone and I was unable to add them or any other.  When I changed the theme again, everything worked.  Try changing themes and see if it works.

EDIT: you shouldn't add the volume control to the system tray, but to the panel.  The system tray is a panel plugin which doesn't allow other plugins inside it.

Thanx! That indeed did the trick, seems all "human" themes block it. Once again thanx a lot.

---

### Post by x1a4 on 2008-06-21
You're welcome.  I hope they fix this soon.  There's a theme I really like but can't use because of this bug.

EDIT: If you feel your issue is solved, mark the thread as resolved.  Click Thread Tools at the top of the thread, then 'Mark thread as resolved'.  And the medal icon at the end of each post, allows you to thank someone for that particular post.  That's where the Thanked count under your avatar in each post comes from.

---

