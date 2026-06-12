---
title: "Menu too long for screen"
date: 2014-07-19
forum: General Help
---

### Post by J._Routh on 2014-07-19
I just installed Lubuntu 14.04 on an Acer Aspire One Netbook (installed alongside original Windows XP). I am playing around with the settings and tried to change the settings of my user account. Under System Tools/Users and Groups/User Settings, I selected my account and clicked on Advanced Settings. On the menu called Change Advanced User Settings, tab 'User Privileges', there is a list of settings to change. However the bottom of the window is hidden on my screen. I can not see the rest of the window nor can I scroll down.

I did some searches first and found out that other people have had similar problems and found you can use the xrandr line command to change the screen resolution. I tried that out but found that my screen is already at the maximum allowed resolution. Typing xrandr displays a list of available settings:

1024x600 (current setting)
800x600
640x480

I tried to change to something larger by using "xrandr --size 1024x768" but received a message "Size 1024x768 not found in available modes". I also tried 2048x1200, no luck either.

I also looked for a command line alternative for changing these advanced user settings but so far have not turned up anything. Any help with changing screen resolution or modifying user settings would be appreciated.

Using command lspci show this information:

Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by Dennis N on 2014-07-19
> **J._Routh said:**
> I just installed Lubuntu 14.04 on an Acer Aspire One Netbook (installed alongside original Windows XP). I am playing around with the settings and tried to change the settings of my user account. Under System Tools/Users and Groups/User Settings, I selected my account and clicked on Advanced Settings. On the menu called Change Advanced User Settings, tab 'User Privileges', there is a list of settings to change. However the bottom of the window is hidden on my screen. I can not see the rest of the window nor can I scroll down.


You can 'grab' the window with the mouse and drag it up:

Put cursor anywhere inside the window. Hold the Alt key down and press and hold left mouse button down at the same time. You can then drag the window up with the mouse and see what's below. To close the window, drag it back down so you can see the closing X. This window has a minimum height (about 800 px) and cannot be resized to less height. There are others like it.

---

### Post by J._Routh on 2014-07-19
Thanks. I didn't know that. That works great!

---

