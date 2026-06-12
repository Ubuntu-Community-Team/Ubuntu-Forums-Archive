---
title: "Windows lockup at random intervals"
date: 2012-12-04
forum: General Help
---

### Post by SOMDdan on 2012-12-04
I am running Ubuntu 12.4, with Cinnamon, on a newish Acer laptop. For six months or so things went swimmingly, but within the past month I have been getting a weird issue with my windows freezing up. I use FireFox as my main browser, and at seemingly random times the computer will not a) open any new widows, no matter what the application, b) will not close any open windows. By "application" I mean ANY application on the computer that opens a window, be it FF, T-Bird, and even native applications like Terminal, or anything else that I have an icon for on the top panel ( often I can't even minimize the window to get to desktop icons). The ONLY way to do anything with the PC when this happens is to CTRL+ALT+F2, to open a shell that way. When I hit a freeze, the mouse pointer works, and I can open drop-down menus on the panel toolbars, but, again, if what I click on requires a new window, it won't respond. The only result that happens when this freeze occurs is that I get a brief flicker at the edges of the screen when I try to open a new window. When I hit a freeze, my only option is to use CTRL+ALT+F2 to open a shell and do "init 6". I can't figure out a way to diagnose the issue during the issue or after a reboot because it is so weird, and I also don't have my regular screens. What to do?

---

### Post by mamamia88 on 2012-12-04
> **SOMDdan said:**
> I am running Ubuntu 12.4, with Cinnamon, on a newish Acer laptop. For six months or so things went swimmingly, but within the past month I have been getting a weird issue with my windows freezing up. I use FireFox as my main browser, and at seemingly random times the computer will not a) open any new widows, no matter what the application, b) will not close any open windows. By "application" I mean ANY application on the computer that opens a window, be it FF, T-Bird, and even native applications like Terminal, or anything else that I have an icon for on the top panel ( often I can't even minimize the window to get to desktop icons). The ONLY way to do anything with the PC when this happens is to CTRL+ALT+F2, to open a shell that way. When I hit a freeze, the mouse pointer works, and I can open drop-down menus on the panel toolbars, but, again, if what I click on requires a new window, it won't respond. The only result that happens when this freeze occurs is that I get a brief flicker at the edges of the screen when I try to open a new window. When I hit a freeze, my only option is to use CTRL+ALT+F2 to open a shell and do "init 6". I can't figure out a way to diagnose the issue during the issue or after a reboot because it is so weird, and I also don't have my regular screens. What to do?
Get a temp monitor and see how hot it is when this happens.  Also get a command line system monitor tool so you can see ram usage etc to see what's going on

---

### Post by irv on 2012-12-04
You could run "top" in a terminal to monitor your running apps and see how much memory there are taking up. It also keeps track of memory usage and swap usage and a few other things.
[ATTACH]228208[/ATTACH]
You can also setup conky, it will keep track of many things happing on you computer. There are thread on this forum to help set it up. Here is what mine looks like.
[ATTACH]228207[/ATTACH]

---

### Post by SOMDdan on 2012-12-04
I will get conky. I doubt that it is a heat or CPU problem because it has happened immediately after a cold restart with nothing running. My first thought was something wrong with the window manager,  (I say that because when I open a shell with CTR+ALT+F2 I can still navigate around my system, but only in the shell) , but I don't know enough to explore that possibility.

---

### Post by irv on 2012-12-04
> **SOMDdan said:**
> I will get conky. I doubt that it is a heat or CPU problem because it has happened immediately after a cold restart with nothing running. My first thought was something wrong with the window manager,  (I say that because when I open a shell with CTR+ALT+F2 I can still navigate around my system, but only in the shell) , but I don't know enough to explore that possibility.

I know this doesn't help your problem, but when you lockup, you can try Ctrl Alt F2 to get to a prompt. you might have to enter your login name and password then you can do a
```
sudo shutdown -r now
```
and your system will clear itself and reboot.
Doing it this way it will close all running processes and give you a nice clean restart.

Edit: I should have also said that if you hit the Ctrl Alt F7 it will bring you back to the GUI.

---

