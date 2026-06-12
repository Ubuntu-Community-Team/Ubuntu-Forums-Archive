---
title: "[SOLVED] Ubuntu 14.04 LTS Stuck on Login Screen"
date: 2015-11-13
forum: General Help
---

### Post by jonathan90 on 2015-11-13
Hello, everyone! I was using Unity Tweak Tool and was messing around with the settings, and when I turned off "window spread" and turned it back on, the screen stopped responding even though the mouse kept moving.  I closed the laptop and reopened it, and when I went to log in, it flashes to my desktop and then returns to the login screen.  However, I can still login through tty1-6 terminals and the guest session works too (which is where I'm writing this from).  Also, the option to load into Unity, Cinnamon or other desktop environments isn't there.

I messed around with commands concerning lightdm last night and managed to login, but the window selection feature wasn't working. By that I mean when you have multiple windows of the same app (like 3 terminals open at once on Unity) and you click on the terminal icon and it lets you pick one.  When I tried to do that, Ubuntu crashed.  I went back into Unity Tweak Tool to try to restore to default settings for the window spread, it crashed again and wouldn't let me login. I forget exactly what commands I used to get it back, so could someone help me out? I did "sudo apt-get install --reinstall lightdm," but I haven't tried to use purge because I'm not sure how to. Thanks!

---

### Post by jonathan90 on 2015-11-13
So I installed GNOME and KDE and booted it on that, and it worked, and so I isolated the problem to Unity Desktop. I simply reinstalled the Unity Desktop and it's in working order again! However, when I boot into Unity, there are traces of KDE "leaking through," such as the scroll bar, the Konsole, the system font, the right click menus, and so on. Anyone know what's going on, or is my Unity Desktop missing files that caused KDE to load in?

---

### Post by Bucky Ball on 2015-11-13
> **jonathan90 said:**
> Anyone know what's going on, or is my Unity Desktop missing files that caused KDE to load in?

No, you installed KDE so unless you uninstalled it, it's still fully there and what is happening would be expected. You would now have a combination of the KDE, Unity and Gnome desktop environments. There no missing files anywhere, just the opposite: a whole bunch of files from the other desktop environments which it sounds like you no longer want.

Uninstall KDE and Gnome. I don't know how easy that is as I think Unity uses some Gnome stuff so some needed things might be inadvertently removed if you totally purge/remove Gnome.

To improve your chances of support, I'd suggest you mark this as solved (see first link in my sig), as your original support request is and you are moving on to a new problem unrelated to the thread title, and start a new thread concerning removing the other two DEs, if you're unsure or get into trouble.

---

