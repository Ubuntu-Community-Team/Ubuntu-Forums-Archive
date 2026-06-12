---
title: "Resume from suspend yields blank screen Xubuntu 14.04"
date: 2015-06-06
forum: General Help
---

### Post by Ralph L on 2015-06-06
Because I spend considerable time on this and it is a common problem in Xubuntu 14.04, I made this forum entry.  There are probably other better fixes, but I did get this one to work (so far).  I am installing xubuntu 14.04 on 2 laptops.  On the Dell Latitude D610 suspend and resume work fine as near as I can tell.  Right now I have light locker settings set to "off" so that I don't need to login after a suspend.  Previously I had it set to "on" and it required password entry on resume, which worked fine. To my knowledge there are 4 settings programs under "Settings" that deal with suspend:  Light Locker Settings, Power Manager, Sessions and Startup, and Settings Editor.  They all have a setting to enable or disable locking the computer on suspend.  I don't know which one does what.
However, on the Toshiba Satellite A215-S4697, when I closed the lid, it suspended fine, but when I opened the lid, I got a blank screen.  Moreover, it didn't do this consistently; sometimes it asked for a password and upon entry then went to a blank screen.  This site discusses the bug and suggests some workarounds: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1357090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1357090) . I tried all of the workarounds and none worked except for the one in post 51 and it was incomplete requiring additional mods as described in this web site changing /usr/bin/xflock4:  [http://askubuntu.com/questions/59577/replace-xscreensaver-with-gnome-screensaver-xubuntu](http://askubuntu.com/questions/59577/replace-xscreensaver-with-gnome-screensaver-xubuntu) . 
Here is what worked for me (taken from post 51):```
1. Install Gnome Screensaver
    sudo apt-get install gnome-screensaver
2. Replace Light Locker with Gnome Screen Saver
    Edited /etc/xdg/autostart/light-locker.desktop
    Change the line from:
         Exec=light-locker
     to:
         Exec=gnome-screensaver
   and then did the same for every existing user
    Edited ~/.config/autostart/light-locker.desktop
     Changed the line from:
          Exec=
       to:
          Exec=gnome-screensaver
3. Edited /usr/bin/xfloc4
     Change these lines from
          # Lock by xscreensaver, gnome-screensaver, or light-locker, if a respective daemon is running
          for lock_cmd in \
               "light-locker-command -l" \
               "xscreensaver-command -lock" \
               "gnome-screensaver-command --lock"
       to
           # Lock by xscreensaver, gnome-screensaver, or light-locker, if a respective daemon is running
           for lock_cmd in \
               "gnome-screensaver-command --lock" \
               "light-locker-command -l" \
               "xscreensaver-command -lock"
3. Hide light-locker-settings from menu for all users using Menu Editor if you want to.
```
Click the mouse or a key to get the full screen display on resume.
If someone else has a better solution, please post it.
Hope this helps someone.

---

### Post by Ralph L on 2015-06-06
EDIT:  THIS METHOD WORKED A FEW TIME, BUT THEN QUIT.  IT IS NOT A SOLUTION.  I ADDED THIS TOO SOON.

Well, I already found a simpler solution, although it has its limitations.
```
In Light Locker Settings set Enable light locker to "on".  Set Lock on suspend to "off.  Click apply.  
Bring up Settings Editor from the Settings Menu
]Click on xfce4-power-manager in left pane.
Set lid-action-on-ac to 1
Set lid-action-on-battery to 1
Set lock-screen-suspend-hibernate to "ticked"
Set logind-handle-lid-switch to "ticked"
Edit ~.config/autostart/light-locker.desktop
Set Exec=
to 
Exec=light-locker
```

This workaround requires that a password always be entered on resume from suspend.
Actually I found later that this would work (at least some of the time) without editing ~.config/autostart/light-locker.desktop

---

