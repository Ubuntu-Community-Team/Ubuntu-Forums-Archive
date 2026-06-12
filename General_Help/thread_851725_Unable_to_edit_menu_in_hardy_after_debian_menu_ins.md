---
title: "Unable to edit menu in hardy after debian menu install"
date: 2008-07-06
forum: General Help
---

### Post by jmjohn on 2008-07-06
Hey all,

I just tried to install the Debian menu.  After installing, I tried to enable it by right clicking the menu and clicking "edit menu".  I can check off whatever I like, but none of the changes apply.  If I return to the edit menu, the checkboxes are now unchecked.

Tried this: ```
sudo update-menus
```

and this: 
```
sudo chown <user> ~/.config/menus
sudo chown <user> ~/.local/share/applications
```

as found here [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97460](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97460)

But no dice.

Anybody know what I should try next?

---

