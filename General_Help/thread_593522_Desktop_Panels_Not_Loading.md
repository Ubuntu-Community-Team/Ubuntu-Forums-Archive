---
title: "Desktop Panels Not Loading"
date: 2007-10-27
forum: General Help
---

### Post by amneziac on 2007-10-27
I did not get this problem when I was on Feisty, but I have had Gutsy for a few days now and today I am having a problem. The top and bottom panels of my desktop arent loading. When I first booted, the panels did not load up at all and I restarted the computer twice. Those other two times that I restarted, the panels loaded, but they are both blank:confused:. Now I don't want a response like "restart your computer until it's fine", because chances are that it might happen again. So what I am looking for is a complete solution so that this never happens again. It's really not a great thing to have when your computer is fully functional and you have to restart the computer because these little things don't load yet I use them a lot. I have to restart manually since the button on the desktop to restart, shut down, log out, etc. isn't there.

---

### Post by anaconda on 2007-10-27
can you get to terminal? or does the Alt-F2 work?

If either of those work you can write 
```
metacity
```
to either of those, and you should get panels working. Desktop effects wont work, because metacity is the default manager without any special effects..

And you can add metacity to startup programs if needed, but I think it isn't necessary, because when you start metacity it will setup itself the default (I think?)

---

### Post by amneziac on 2007-10-27
well I tried what u said (except I said metacity --replace) and I got this error
[code]
kenan@kenan-desktop:~$ metacity --replace
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
[code/]
Kiba Dock gets loaded everytime and I have the beryl manager launcher on it, when I change manager to metacity, it works, but still nothing happens with the panels. So #1, why doesnt metacity change work in terminal but it works when i change window manager in the beryl manager, #2 why the hell isn't this problem solved.
I restarted another 3 times, and now the panels wont load at all.

---

### Post by amneziac on 2007-10-27
Can I please get more help?

---

