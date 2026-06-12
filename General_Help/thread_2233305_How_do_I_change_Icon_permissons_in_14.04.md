---
title: "How do I change Icon permissons in 14.04"
date: 2014-07-07
forum: General Help
---

### Post by RogerDavis on 2014-07-07
I need to change icon permissons so I can use the transplanted icon.

---

### Post by Frogs Hair on 2014-07-07
A little more info would help , but generally permissions are found by right clicking and entering properties . Location and account type may affect the ability to change permissions .

---

### Post by RogerDavis on 2014-07-07
Sorry for the lack of info.  

Using Ubuntu with Gnome Flashback Metacity, I drug several icons onto the desktop.  All the others worked, but this one didn't.  This one is shown as root, and I need to make it usable for everyone.

I can't alter the properties, as I'm logged in as administrator, not root.  I thought maybe I could do a "sudo" in terminal, but then how would I get that to apply to the GUI?  Harry Potter I ain't, so I make every effort to do something straightforward without calling on the dark side...

Thanks!

I didn't have much time, so I just posted this quickly and left to make my appointment.

---

### Post by Bucky Ball on 2014-07-07
Easiest way is to launch your file manager from a terminal as root. If you're using Nautilus, try this:

```
gksudo nautilus
```

Now you can change the permissions as you want. BUT ... BE CAREFUL! Do what you need to do and close that file manager. You are logged into it as root and can cause serious damage and breakage if you go astray.

---

