---
title: "Trashed a user profile...need help recovering"
date: 2007-09-22
forum: General Help
---

### Post by djxcon on 2007-09-22
hello...need some help here.  I was disabling beryl from my session startup, clicked on the save session button when everything was just right, and now when i try to log on...i get a splash screen with about 9 metacity icons.  

I am not able to reach the desktop upon signing and eventually I get kicked back to the login page.  Other user profiles on the system are fine so it's just this one...how can i recover from this?

I'm hoping to do this without recreating the profile from scratch.

---

### Post by HermanAB on 2007-09-22
The easiest solution is to create a new user and copy the data over.

Cheers,

H.

---

### Post by djxcon on 2007-09-22
SOLVED: In order to restore a default gnome session, I ran the following code:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Then I was faced with the message about the gnome panel already running so I had to kill those processes as well.

```
ps aux | grep panel
```

I killed all processes except for 1 gnome panel process.  Pressed (CTRL ALT Backspace), logged in, and everything was working.

---

