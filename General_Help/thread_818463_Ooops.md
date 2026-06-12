---
title: "Ooops"
date: 2008-06-04
forum: General Help
---

### Post by Mike.42 on 2008-06-04
I acedently installed FluxBox 1.0. How can I uninstall this? Now whenever I log in as my user, the screen is complety gray with a bar on the bottom. What comand can I run in the terminal to uninstall this and get my desktop back to normal?
Thanks, 
Mike

---

### Post by wolfen69 on 2008-06-04
```
sudo apt-get remove --purge fluxbox
```

---

### Post by forestpixie on 2008-06-04
Logout and when you get to the login screen, form the bottom left (I think) choose sessions - then pick gnome - enter username and password as normal then make gnome default.

Now you can uninsatll from sysnaptic or the terminal

```
sudo apt-get remove fluxbox
```

Edit - I'm off to the pub if I'm going to be a minute behind you all night :)

---

### Post by Mike.42 on 2008-06-04
Thanks a lot it worked.

---

