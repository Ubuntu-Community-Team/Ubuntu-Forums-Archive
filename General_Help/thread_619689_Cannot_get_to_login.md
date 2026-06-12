---
title: "Cannot get to login"
date: 2007-11-21
forum: General Help
---

### Post by rudeboyskunk on 2007-11-21
Ok, so Ubuntu boots up and everything.  Then it refreshes the monitor to go to the login screen, but instead of starting X, it just is a black screen with the cursor blinking in the top left.

I am using Ubuntu Gutsy Gibbon 7.10.  It was working fine as of last night.  I have never had this problem before.  I'd prefer not to do a clean install if I can help it.  Any thoughts?

---

### Post by taurus on 2007-11-21
Press <Ctrl><Alt>F2 and login with your username and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to the GUI login screen with <Alt>F7 and restart X with <Ctrl><Alt>Backspace.  Do you see the GUI login scree now?

---

### Post by rudeboyskunk on 2007-11-21
That's just it, I tried doing that, and nothing happened.  The screen didn't even refresh.  It just stayed where it was.  I can turn num lock on and off though.

---

### Post by rudeboyskunk on 2007-11-21
*bump*

---

