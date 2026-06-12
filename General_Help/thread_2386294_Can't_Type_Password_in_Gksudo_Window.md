---
title: "Can't Type Password in Gksudo Window"
date: 2018-03-03
forum: General Help
---

### Post by marnsghol on 2018-03-03
After upgrading to _**Ubuntu 17.10**_ I can't type in my password into the **Gksudo** window.
I use a gnome version 3.62.2 if thats relevant.
Example:[INDENT]>> gksudo gedit ~/.bashrc
*window opens*
*type password, it shows up in terminal instead*
*click on the window text field, type password, still shows up in terminal instead*
*click enter to try it, nothing happens*

[/INDENT]

---

### Post by Frogs Hair on 2018-03-03
Try from the Ubuntu on Xorg session if gksu is installed. To grant temporary permissions in the wayland/Ubuntu session use the following first. ```
 xhost +si:localuser:root
```

---

### Post by kerry_s on 2018-03-03
why are you editing your .bashrc as root?

wayland session does not allow root like that, you can do it the wayland way "gedit admin:///your-file"
or
select xorg session to do it the old way

---

### Post by marnsghol on 2018-03-04
Worked, seems like wayland was indeed the problem. Thank you for the quick response !

---

