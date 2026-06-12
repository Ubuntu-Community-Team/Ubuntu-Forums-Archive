---
title: "Cairo Dock question involving desktop icon placement"
date: 2013-08-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-08-02
Is there a way to prevent this from happening?
[IMG]http://i.imgur.com/LJuDusC.png[/IMG]

---

### Post by Toz on 2013-08-02
Thinking outside the box.....

How about a transparent empty xfce4-panel on the left side of the screen. It would push out the icons.

---

### Post by pqwoerituytrueiwoq on 2013-08-02
Wouldn't that make windows not use the same space?

---

### Post by Toz on 2013-08-02
> **pqwoerituytrueiwoq said:**
> Wouldn't that make windows not use the same space?
Yes. When opening new windows, they won't overlap the panel (and cairo bar), but you can still move the window there. Or you can disable struts and the windows will ignore the panels. More info on disabling struts [here]("http://forum.xfce.org/viewtopic.php?id=6603").

---

### Post by pqwoerituytrueiwoq on 2013-08-02
if i disable struts the panel covers everything, windows, cario dock, and desktop icons
if i don't windows don't occupy that space, defeats the purpose
i use the my desktop for temporary files so i would rather deal with this issue then use a xfce panel like that

---

### Post by stinkeye on 2013-08-05
What about disabling desktop icons and using the cairo-dock folders applet to show the 
contents of your desktop folder.
Can show contents when applet hovered or detach for a permanent desklet.

---

### Post by pqwoerituytrueiwoq on 2013-08-05
> **stinkeye said:**
> What about disabling desktop icons and using the cairo-dock folders applet to show the 
contents of your desktop folder.
Can show contents when applet hovered or detach for a permanent desklet.
now there is a good idea
if it would show flash drives that would be perfect
i know shortcuts can do something like that, but it list my main drives and empty sd card and dvd drive
Edit: anyone know a way to do this via the theme?
i was messing with ~/gtkrc-2.0
i got the idea from [this]("http://www.dedoimedo.com/computers/xubuntu-pimp.html"):
```
style "xfdesktop-icon-view" {
        XfdesktopIconView::label-alpha = 0
        
        fg[NORMAL] = "#ffffff"
        fg[SELECTED] = "#ffffff"
        fg[ACTIVE] = "#ffffff"
        }
        
        
        widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

---

