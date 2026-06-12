---
title: "application on tint2 bar"
date: 2014-12-30
forum: General Help
---

### Post by sreejith-sadasivan on 2014-12-30
Hi,
I have some application on the tint2 bar. if I right-click one icon then the application will get closed.
I dont want this to happen. but by right-clicking the tint2 bar, the application icon should disappear from tint2 bar but it should be running in the background.
is there anyway to do this ?

---

### Post by vasa1 on 2014-12-30
Configuration is done by means of ~/.config/tint2/tint2rc. Whatever is possible is listed there. For mouse actions, there is:```
#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify
```

---

### Post by sreejith-sadasivan on 2014-12-30
Hi , thanks.

but if  "mouse_right = close"  will close the entire application . instead I want the application to run in background and show it in system tray on top right of the screen so that whenever I click the icon the application should appear in tint2 bar again. is there anyway to do this ?

---

### Post by vasa1 on 2014-12-30
> **sreejith-sadasivan said:**
> Hi , thanks.

but if  "mouse_right = close"  will close the entire application . instead I want the application to run in background and show it in system tray on top right of the screen so that whenever I click the icon the application should appear in tint2 bar again. is there anyway to do this ?
If I understand both your posts correctly, they're are different in what they are asking for.

---

### Post by sreejith-sadasivan on 2014-12-30
the issue is same. my issue is : if I right-click an application in tint2 bar , it is getting closing . it may be because the setting "mouse_right = close" .
my requirement is : if I right-click an application in tint2 bar, it should disappear from the tint2 bar but it should not completely close(shutdown). its icon should be displayed somewhere at the top right of the desktop so that if i click there next time , the application should re-appear at the tint2 bar. hope this is clear .

---

### Post by kerry_s on 2014-12-31
he wants it to minimize, so its toggle or iconify he needs to change it to.

---

