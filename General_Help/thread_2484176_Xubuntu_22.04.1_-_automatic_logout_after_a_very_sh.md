---
title: "Xubuntu 22.04.1 - automatic logout after a very short period of inactivity"
date: 2023-02-19
forum: General Help
---

### Post by wheelright on 2023-02-19
Hello all - my first post here.

I recently installed Xubuntu 22.04.1 LTS on my old ACER laptop - previously I'd been using 16.04 LTS

With the new version of the OS, I'm finding that I get logged out - i.e. have to input my admin password again - after only a very short period of mouse/keyboard inactivity (5 minutes).  As I live alone and I'm the only person who uses this machine, I'd like to extend this to something practical, like 30 minutes or so.

I figured that this might be achieved by changing a setting in Power Manager or maybe Users & Groups, but can't find anything there.  Does anyone know how I can achieve what I'm after?  A Terminal command, perhaps?  Any and all advice gratefully received. :)

---

### Post by Holger_Gehrke on 2023-02-19
I'd take a look in 'Settings'->'Screensaver' (the program called by this menu item is 'xfce4-screensaver-settings'; you can call it from a terminal if for some reason there's no menu item for it). Could be that you've switched on locking or even have it set to log you out ...

Holger

---

### Post by wheelright on 2023-02-19
Dear Holger - thank you so much for your help, which has solved my problem.  I would never have guessed that this behaviour came under "Screensaver" settings.  I now have a machine that switches off the display after 5 minutes (I've no problem with that), but does not require me to log in again every time.

Thanks again - much appreciated. :)
wheelright

---

### Post by ajgreeny on 2023-02-19
All the settings mentioned here are available in the **Settings-Manager** in your menu
**Screen-lock** is also  a setting in the System tab of the **Xfce4-power-manager** as well as **Screensaver** so have a look there as well.

Should you ever need or wish to secure your machine from others around you, you can use the Lock-Screen key combination, **Super(Winkey) + L** on my laptop but I may have changed it from the default whatever that was.
You can find your current shortcut setting in your keyboard settings from **Settings-Manager.**

---

### Post by wheelright on 2023-02-19
Many thanks for the further advice, ajgreeny - I'll check it out. :)

---

