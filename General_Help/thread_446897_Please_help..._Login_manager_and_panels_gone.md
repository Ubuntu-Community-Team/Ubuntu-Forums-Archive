---
title: "Please help... Login manager and panels gone"
date: 2007-05-17
forum: General Help
---

### Post by monaleilani on 2007-05-17
After upgrading to FF, my login manager and panels have disappeared. 
When I boot, it goes to a tan screen and nothing else. That was where my custom login manager used to be.
The only way I can get on my desktop is to press ctrl+alt+f1,  I login to my account, stop GDM, then do startx. My desktop appears, but with no panels. I can create launchers and browse files, but that's about it.
I'm aware this is an upgrade issue, but I posted in there and noone helped me. I should mention before I upgraded I had a custom theme and a custom login manager.
Someone please help me.. I've been struggling with this issue for days.

---

### Post by ceelo on 2007-05-17
Not sure if this will be the answer, but try accesing a terminal and issuing a "killall gnome-panel", then running "gnome-panel" to start it up. I had a similar issue to where whenever I restarted X and logged back into gnome, I would get no panels. That seemed to fix it (until I restarted X again)

---

### Post by kvonb on 2007-05-17
Maybe try re-setting your xorg.conf.

At the term type this:

```
sudo cp /etc/X11/xorg.conf .etc.X11/xorg.conf.xxxx
sudo dpkg-reconfigure xserver-xorg
```

If you had any of the old compiz or Beryl stuff on there before the upgrade it might be causing a problem

If it doesn't work, simply delete the new xorg.conf and rename the .xxxx one to xorg.conf to get it back.

---

### Post by monaleilani on 2007-05-17
ceelo, I've tried killing gnome-panel before and rerunning it.. Kept saying it found a panel already running. :(
I'm sure that the custom login manager and the theme still work. A little while ago I somehow managed to make everything work. But then when I rebooted, it was back to the same thing again.

---

### Post by monaleilani on 2007-05-17
> **kvonb said:**
> Maybe try re-setting your xorg.conf.

At the term type this:

```
sudo cp /etc/X11/xorg.conf .etc.X11/xorg.conf.xxxx
sudo dpkg-reconfigure xserver-xorg
```

If you had any of the old compiz or Beryl stuff on there before the upgrade it might be causing a problem

If it doesn't work, simply delete the new xorg.conf and rename the .xxxx one to xorg.conf to get it back.

It didn't work. I didn't really know what to answer for alot of the xorg configuration stuff. When I was done I restarted x and everything was black, had to restart.

---

### Post by monaleilani on 2007-05-17
I got my login manager and panels to work again, but I know when I restart the settings will be gone. I got back to my login manager and menus when I restarted gdm while in Ubuntu. Any way to save and permanently implement the current settings? I hate that when I restart this will be back the way it was...

---

