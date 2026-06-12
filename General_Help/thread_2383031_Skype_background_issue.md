---
title: "Skype background issue"
date: 2018-01-20
forum: General Help
---

### Post by tominto on 2018-01-20
I have the newest version of Skype on 16.04.  When I launch skype, initially all I get is the skype window, but with my desktop background.  I can move this window around my desktop, and the background image will move along within the window.
Only after I minimize and then maximize the window does the proper skype interface appear and I can continue normally.  What's going on here and how can I fix it?
Thanks

[IMG]http://i66.tinypic.com/2n8psoh.jpg[/IMG]

:confused:

---

### Post by kostkon on 2018-01-20
Let's make sure you are using the latest version. Type this command in a terminal and paste the output:
```
apt policy skypeforlinux
```

You could try disabling the option *Start Skype in the background* (Tools &#8594; Settings...), if it is on. It can cause problems on some systems.

---

### Post by tominto on 2018-01-20
Disabling start skype in background solved it.  Thanks

---

