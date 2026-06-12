---
title: "A locally logged in user can run x0tigervncserver. An ssh user not."
date: 2020-09-29
forum: General Help
---

### Post by 90v45mfsdhbgsd on 2020-09-29
Lubuntu 20.04, lxqt login as zoe.
When I run
x0tigervncserver --rfbauth=/home/zoe/.vnc/passwd
it works and I can connect from another PC.

Now I stop the x0tigervncserver with control-c.
I remain loggen in in lxqt.

I logged in also with ssh from another PC and run exactly the same command.
Now it says something like cannot found display "".

Exactly the same error displays when I create a systemd service for x0tigervncserver and run systemctl enable/start/status. All of them (enable/start/status) with loaded lxqt and user logged in.


It seems that when run the command from ssh console or when run the command with systemd, X is not available for some reason, so it cannot found display "". But X is loaded because lxqt is loaded.

What I miss here?

---

### Post by TheFu on 2020-09-30
X11 is tied to the X/session.  There are 2 things needed to accomplish that.
Set the DISPLAY environment variable and have the ~/.Xauthority file "secret" known by any client programs.

There is no way to do that from systemd that I know. sorry.

But vnc sucks, so why bother when there are better answers?  Use x2go instead. It is faster and 100x more secure and just a few commands to setup once ssh works.

---

