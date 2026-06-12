---
title: "[SOLVED] Open GUI program over SSH"
date: 2008-06-27
forum: General Help
---

### Post by altonbr on 2008-06-27
If I can run ```
xwd -out screenshot.xwd -root -display :0.0
``` to take a screenshot of the current X screen, how can I open a program, such as gedit or dolphin to that same screen?

IE: I want to show someone dolphin in KDE 4.1 but they don't want it on their computer.

That's one of the uses anyway.

---

### Post by kbuel on 2008-06-27
You can open a GUI application over ssh by simply using the -X flag.

ssh -X user@server

then when you run the application the GUI should display.

---

### Post by tamoneya on 2008-06-27
its also typically a good idea to use compression on the ssh as well when you allow X11 forwarding.  Makes it play nicer with your internet:
```
ssh -X -C user@server
```

---

### Post by altonbr on 2008-06-28
Thanks guys, I was wondering what that was for. I assumed it was VNC or something, but I was wrong!

---

