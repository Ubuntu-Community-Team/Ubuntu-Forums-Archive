---
title: "Show Debian Menu"
date: 2008-05-01
forum: General Help
---

### Post by Anzan on 2008-05-01
I find having the Debian menu show in the Applications menu useful. I had enabled this previously but I have a fresh Hardy install and cannot remember how and a Google search yeilded nothing.

(Clicking it in Edit Menu or System/Preferences/Main Menu does not work.)

---

### Post by RATM_Owns on 2008-05-01
Goto System->Preferences->Main Menu and under the Applications thing (should be in the main screen when you choose Main Menu) tick the Debian thing.

EDIT: Didn't read that. I think you need a program or something under the Debian option.

---

### Post by Ziggy72 on 2008-05-01
Ensure that menu-xdg  and menu are installed (synaptic). Then:	
```
sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg
```
Now, to make the menu show up, it is not necessary to reboot - just type:
```
killall gnome-panel
```

---

### Post by Anzan on 2008-05-02
Thanks, Ziggy72. I had installed menu-xdg but not menu. Once I had, I did not even need to reconfigure.

---

