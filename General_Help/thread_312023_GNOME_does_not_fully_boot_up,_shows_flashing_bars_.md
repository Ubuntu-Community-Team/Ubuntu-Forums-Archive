---
title: "GNOME does not fully boot up, shows flashing bars on top and bottom"
date: 2006-12-03
forum: General Help
---

### Post by kirkio on 2006-12-03
I have a GNOME/KDE setup and I just changed the font sizes to use in KDE and ended my session. When I logged in to GNOME everything was fine, but when the bars on the top and bottom appeared, they were solid light-gray (no text or icons) and blinked for a while, then they stopped blinking at all and disappeared, leaving no icons on the screen and no accessibility whatsoever. I can still log into KDE and it works fine. What could this problem be isolated to? Nautilus? and how would I go about fixing it. Thanks.

---

### Post by mssever on 2006-12-03
> **kirkio said:**
> I have a GNOME/KDE setup and I just changed the font sizes to use in KDE and ended my session. When I logged in to GNOME everything was fine, but when the bars on the top and bottom appeared, they were solid light-gray (no text or icons) and blinked for a while, then they stopped blinking at all and disappeared, leaving no icons on the screen and no accessibility whatsoever. I can still log into KDE and it works fine. What could this problem be isolated to? Nautilus? and how would I go about fixing it. Thanks.Hmmm... What happens

1. If you log into KDE and then type gnome-panel into a terminal?

2. If you log into Gnome and type ```
kill $(pidof gnome-panel)
gnome-panel
``` You might have to repeat the kill command several times to make the panel quit, or even use kill -9.

---

### Post by kirkio on 2006-12-04
Logging into KDE and running gnome-panel loads the GNOME bars and they function.

How would I run the kill command if I am logged into the GNOME Interface and can't access the icon for the terminal? Is there a keyboard shortcut to get me to the shell?

Thanks

---

### Post by mssever on 2006-12-04
> **kirkio said:**
> Logging into KDE and running gnome-panel loads the GNOME bars and they function.

How would I run the kill command if I am logged into the GNOME Interface and can't access the icon for the terminal? Is there a keyboard shortcut to get me to the shell?

Thanks

If you hit Alt+F2, you'll get the run dialog. Type gnome-terminal.

You might also want to check to see if nautilus and gnome-panel are running ```
ps -ef | egrep '(nautilus|panel)'
```

---

### Post by kirkio on 2006-12-05
Alt + F2 does not yield a run dialog. What should I do?

---

