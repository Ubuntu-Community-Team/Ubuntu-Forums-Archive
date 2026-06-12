---
title: "How to change the ubuntu notification bubble."
date: 2013-08-21
forum: General Help
---

### Post by adrian89 on 2013-08-21
I've install xubuntu-desktop on my ubuntu laptop.
The problem is that it changed the notification bubble from unity one to the xfce4 one.Is there a way to change it back?

---

### Post by vasa1 on 2013-08-21
I don't know the answer but may I ask why you want the Unity one back? 

I understand that the one you get with xubuntu-desktop is far more configurable:
[LIST]
[*]You can change the "gravity" or where you want the bubble to appear (TL, TR, LR, LL).  
[*]You can change the time the bubble stays on-screen.
[*]There are also themes available to customize the appearance of the bubble. I see /usr/share/themes/Smoke/xfce-notify-4.0/gtkrc.
[*]
[/LIST]

If you uninstall `xubuntu-desktop`, the notification bubble may revert to the Unity one but that's **just a guess**.

---

### Post by adrian89 on 2013-08-21
[SIZE=2][FONT=arial]I use Unity as default desktop environment,as for Xubuntu I use it for movies since the playback(for HD movies) is much better then on Unity.
I'm used to the Unity bubble so that is why I want to change it.

Found the solution:

```
[COLOR=#3B3B3B]gksudo gedit /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service
```

After that change line :

[/COLOR]```
Exec=/usr/lib/xfce4/notifyd/xfce4-notifyd
```[COLOR=#3B3B3B]
With:
[/COLOR]```
Exec=/usr/lib/x86_64-linux-gnu/notify-osd[/FONT][/SIZE]
```

---

### Post by vasa1 on 2013-08-21
You should mark the thread as SOLVED because others would benefit from your solution.

---

### Post by adrian89 on 2013-08-21
yeah I forgot.

---

