---
title: "No windows borders after yesterdays Compiz update"
date: 2008-05-29
forum: General Help
---

### Post by Kaisersoze on 2008-05-29
Hi, 

Yesterday I accepted a system update on compiz. After this system update, I no longer have windows borders with the minimize, maximize and close buttons. My keybod is always set to some weird profile, etc...

I had this problem before and somehow managed to work it out through removing compiz and reinstalling it again. this seems not to work now. Compiz --replace doesnt work also.

Anyone has an idea on how so fix this? its kinda annoying...

Thank you

---

### Post by LeoSolaris on 2008-05-29
That is a bug I have been dealing with randomly for a few weeks. All you have to do is go to Compiz config and turn the Windows Borders off, then back on and they should appear. Alternatively you can just log out and back in.

The profile of your keyboard is not something I have experienced, so I can't help there.

Leo

---

### Post by mikeric on 2008-05-29
Mine has been ddoing the same thing, only with firefox though, no other windows. i have been restarting, but havent tried just logging out yet.

---

### Post by Forlong on 2008-05-30
If something like that happens, run ```
compiz-decorator --replace
``` via [Alt]+[F2]

---

### Post by Kaisersoze on 2008-05-30
Hi, 

Yesterday I have installed emerald and now system always boots ok with emerald. Going to stick with compiz and emerald for a while! :-)

Thank you all

---

### Post by Kaisersoze on 2008-05-31
Welll, seems I have losted it again... now system boots with no borders by default again!

I have to load compiz fusion icon, the switch to "metacity" then to Compiz again to have borders.

This bug is very, very very annoying... 

compiz-decorator --replace wont do the trick since the damn machine will boot again with no borders.

Seems to me this has something to do with a conf file because when I installed Emerald it went smoothly for a couple of days until the system writes "something in somewhere" from here system will boot with invalid compiz settings.

If we load compiz again it will load with good settings.. weird huh?!:confused:

---

### Post by Forlong on 2008-06-01
Make sure the **Window Decoration** plugin is enabled and insert the window decorator of your choice (gtk-window-decorator, kde-window-decorator or emerald) in the field next to **Command**

---

### Post by sayakb on 2008-06-01
Open ccsm and goto Preferences. Select *reset to defaults*.

---

### Post by Northsider on 2008-06-02
Ugh, this has been annoying me to no end...thanks for the info.

---

### Post by andreyves on 2008-06-23
I got the same problem, here is the easy way to fix that, to got that solution working I am presuming that you alredy configured your nvidia driver, so /etc/X11/xorg.conf must alredy use the nvidia driver. Not sure yet, but this seem to happen only with the nvidia driver...

1) Type CTRL-ALT-F1 to got a working console
2) Log-in with your username and your password
3) Type sudo apt-get remove nvidia-glx
4) Type sudo apt-get install nvidia-glx-new
5) Just reboot the computer

Andre Yves Cloutier

---

