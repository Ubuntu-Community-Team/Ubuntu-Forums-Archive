---
title: "Logoff/Shutdown Button"
date: 2006-10-14
forum: General Help
---

### Post by hawks1282 on 2006-10-14
I have a recent install of Ubuntu (Dapper Drake 6.06) running on my computer.  I recently installed Beryl and Kiba Doc and now whenever I press the power down button in the upper right hand corner of the screen the entire system freezes and I have to hit the restart button.  Has any one had this problem or know how to fix it? Thanks

---

### Post by evilghost on 2006-10-14
I know this was the case when runing xcompmgr so this may/may not apply but basically with xcompmgr the problem was metacity would draw the logout screen without showing it on the desktop (I can't remember the exact root cause).  I bet this is your case, try hitting "Esc" next time you are "locked up" and see if the sysem returns to a normal usable state.  If so you may need to stop Beryl prior to logging out/shutting down.

---

### Post by hawks1282 on 2006-10-15
That seems to be exactly whats happening.  When I turn off Beryl it works fine (escape also un-freezes the system)  Thanks for your help

---

### Post by evilghost on 2006-10-15
> **hawks1282 said:**
> That seems to be exactly whats happening.  When I turn off Beryl it works fine (escape also un-freezes the system)  Thanks for your help

Glad to help.  If you happen to find a resolution to the issue please update this thread.  Last time I researched I was told this was expected behavior (even though it's undesired) and there really isn't a fix.  Metacity is the culprit.

---

### Post by twstokes on 2006-11-08
If you shutdown from the panel, here's a script that I made to solve the issue for me.

```
#!/bin/sh

killall xcompmgr
gnome-session-save --kill
```

Replace the logout applet with a Custom Application on the panel that is the path to this script, and change the icon to the logout icon.

---

### Post by Cyr4x on 2006-12-03
That's good, but how to applay this script to main menu? I don't have a close icon on the panel, always doin' it from main menu.

---

### Post by twstokes on 2006-12-03
That's a good question - and I'm not really sure.

---

### Post by CatKiller on 2006-12-03
As an alternative, you could just learn the keyboard shortcuts: Once you've selected Quit from the menu, it's

Alt-L to logout
Alt-R to restart
Alt-S to shutdown

Alt-O to lock the screen
Alt-W to switch user
Alt-H to hibernate

---

