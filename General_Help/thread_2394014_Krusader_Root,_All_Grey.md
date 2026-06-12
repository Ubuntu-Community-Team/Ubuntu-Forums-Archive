---
title: "Krusader Root, All Grey"
date: 2018-06-11
forum: General Help
---

### Post by webmanoffesto on 2018-06-11
I'm using Ubuntu 16 Gnome. I like the Krusader file browser, but when I try to run it in root it opens as only a grey screen. I found

"As noted in the previous post I discovered that the problem was related to compositing and this was resolved in a normal desktop session by disabling compositing - opening krusader in root mode (success) and then re-enabling compositing after which Krusader opens successfully each time. To resolve this in a VNC session requires opening krusader with kdesu QT_X11_NO_MITSHM=1 krusader
This can also be added as a user action in the Krusader settings Konfigurator menu and a meta key configured for faster access. 
This will apply to other applications that open with a blank grey window using kdesu in a vnc session.
Hope this help others who encounter this problem." [https://forum.kde.org/viewtopic.php?t=140628](https://forum.kde.org/viewtopic.php?t=140628)

In Krusader, I go to Settings / Configure and that opens the Konfigurator. But I don't see what to do next.

Gnome Commander Works fine in root, but sometimes I prefer Krusader.

---

