---
title: "Deleted my wine menu, halp!"
date: 2007-12-05
forum: General Help
---

### Post by FoxHappy on 2007-12-05
I deleted my wine menu from under applications, how do I get it back?
I know about Edit Menus, but I don't know how to get my wine menu back.

________________________
Edit:

Ah ha! Finally found it. For anyone else that has this problem, after wine is installed:

```
sudo apt-get --purge remove wine
sudo rm -r /home/username/.config/menus
```

Then Log Off and and Log On back to restart the desktop.

And it's right back where it should be :)

---

### Post by rsk02 on 2008-03-20
Caution!! The code provide in the previous post completely removes your Wine installation AND your Wine directory.

---

### Post by acheong87 on 2008-05-15
Also, doesn't that completely reset all your menu configurations?!  I'm not sure, and I don't want to risk it.  Instead of removing the entire menu directory, just remove the "wine" section in /home/username/.config/menus/applications.menu.

---

### Post by dogeth on 2008-07-05
This worked for me!

I reinstalled wine next, and back to normal.

---

