---
title: "Can Not Open Terminal In 14.04"
date: 2015-07-23
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-07-23
Hello,

I can not open a terminal in 14.04 with ctl + alt +t more than once during a session, in Ubuntu Classic Gnome; although I can still open a terminal with Applications > Accessories > Terminal as many times as I want.  In fact I have tried rebooting three times and the behavior persists.  This is a dual boot system, so I booted into Windows 7 to verify that I was not having keyboard or touchpad problems.  All the hardware worked fine in Windows.  BTW, I have also been having touchpad problems in 14.04; i.e., I often have to tap on the touchpad several times to get the cursor to "stick" when trying to move a scollbar slider.  It also seems possible that the problem could be with the Window Manager as well.

Thanks, Hannibal

---

### Post by mansonfan78 on 2015-07-23
Try setting the keyboard shortcut to something else, there may be some other application that might be conflicting with it.

---

### Post by coljohnhannibalsmith on 2015-07-24
This appears to have done the trick.  I selected ctl + alt + y, because it's right next to the t.

I hate it, but it works.

BTW, it also seems like the cursor is sticking to the scroll bar slider like it's supposed to now; but I'm going to wait a little longer before I rejoyce.

Thanks, Hannibal

---

### Post by CantankRus on 2015-07-24
In one of your other threads I advised you to use **own_window_type normal** in your conky config.
I've noticed lately that when conky is running and you close a window to reveal the desktop some keyboard shortcuts fail.
Clicking on the desktop allows the keyboard shortcuts to work again.
Something to do with conky stealing the desktop focus.

_**Solution**_:
Go back to using **own_window_type [COLOR="#FF0000"]override[/COLOR]** in your conky config

[SIZE=3]or[/SIZE]

Use the ccsm window rules plugin to give conky no focus when using **own_window_type [COLOR="#FF0000"]normal[/COLOR]**
```
class=Conky
```
[ATTACH=CONFIG]263343[/ATTACH]

The window rules plugin is only available when compiz-plugins is installed.
```
sudo apt-get install compiz-plugins
```

---

### Post by coljohnhannibalsmith on 2015-07-24
Wow,

It seems like Ctl + Alt + T is working again.  I wasn't sure whether or not I would be able to capitalize the "C" in Conky as you did; but for now it appears to be working.

_**Solution**_:
Go back to using **own_window_type [COLOR=#FF0000]override[/COLOR]** in your conky config.

The above just brought back the instability problem I was having before.

Thanks, Hannibal

---

### Post by CantankRus on 2015-07-24
> **coljohnhannibalsmith said:**
> Wow,

It seems like Ctl + Alt + T is working again.  I wasn't sure whether or not I would be able to capitalize the "C" in Conky as you did; but for now it appears to be working.

_**Solution**_:
Go back to using **own_window_type [COLOR=#FF0000]override[/COLOR]** in your conky config.

The above just brought back the instability problem I was having before.

Thanks, Hannibal

I use **own_window_type normal** in all my conky configs and apply the 3 ccsm tweaks as shown 
in your conky thread and here.
Goodluck ;)

---

