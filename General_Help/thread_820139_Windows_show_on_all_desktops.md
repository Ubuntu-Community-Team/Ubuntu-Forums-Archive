---
title: "Windows show on all desktops"
date: 2008-06-06
forum: General Help
---

### Post by eklypze on 2008-06-06
Hi everyone,
I'm currently using Kubuntu 8.04 with compiz enabled, and currently have a total of 4 virtual desktops. However, no matter what desktop I am on all windows are visible on the taskbar and thus cluttering my entire workspace.

Is there a way to keep each window only to their respective desktops? Thanks.

---

### Post by mojoman on 2008-06-06
This sounds like an easy configuration issue though I rarely use KDE so I can't tell you exactly how to change it. Have a look at the "settings" part in the KDE menu. Most likely you should be able to configure this under "desktop/panels" or something like that.

/mojoman

---

### Post by merike on 2008-06-07
There's some compatibility issue between Compiz and that option as far as I gathered from searching around.

I settled for the following:
- installed kicker-taskbar-compiz from universe
- removed usual taskbar aplet from panel
- added taskbar-compiz to panel
- opened /home/yourusername/.kde/share/config/ktaskbarrc and added the following:

[General]
ShowAllWindows=false

- Ctrl+Alt+Backspace to restart kde

It works with a small lag when switching desktops so for about half a second you'll see windows from previous desktop and then they switch for new ones.

---

### Post by i speak in math on 2008-06-07
I haven't used K yet, but in gnome, if you right click in your window list (i can usually right click just to the left of the first thing open) there is an option for exactly what you are asking. You can choose, "show windows from every desktop" or "show windows from only current desktop". Perhaps there is a similar option in K.

---

