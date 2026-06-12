---
title: "Problem remote controlling local Ubuntu machine"
date: 2012-10-22
forum: General Help
---

### Post by mar_ar on 2012-10-22
I moved to Ubuntu on my local machines at home.
I have 1 desktop computer with no monitor,mouse or keyboard attached, and two laptops.
The idea is to run the heavy tasks (compilation, long downloads etc.) on the "server" (the desktop) and control it by the laptops.

I have open SSH on the desktop.
I have no problem connecting by SSH to the desktop.

_I tried two methods of remote controlling the desktop:_

[LIST]
[*]**X Server** - I run ssh -X user@host and run any application I want - this is very slow! 
[*]**VNC** - using the built in mechanism in Ubuntu - this works only after booting the desktop with monitor connected. If I reboot without connected monitor, I can't connect. I tried to load the X Server on the machine (startx) and got an error.
[/LIST]

_My questions are:_
[LIST]
[*]1. What is the fastest way to connect to local machine (terminal)? (SSH seems like an overhead).
[*]2. How can I remote control the computer even thought there is no monitor connected?
[*]3. What is the best way to share files on the desktop with the laptops?
[/LIST]
Thanks.

---

