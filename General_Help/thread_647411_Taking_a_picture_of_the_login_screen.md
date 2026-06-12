---
title: "Taking a picture of the login screen?"
date: 2007-12-22
forum: General Help
---

### Post by Fireblend on 2007-12-22
Hey, I'm currently using my own GDM login screen I created. However, I'd like to make some modifications to it based on the location of the user/password input box. Is there any way I could get a screenshot/complete preview of the login screen? So far I have calculated it, but I'd have way better results if I could get a screenshot to compare changes with :p.

Thanks in advance!

---

### Post by Bolorino on 2007-12-22
Hi Fireblend,
try this:
Open a virtual term (Ctrl+Alt+F1)
Login with your username and password

```
DISPLAY=:0 import -window root filename.png
```

---

