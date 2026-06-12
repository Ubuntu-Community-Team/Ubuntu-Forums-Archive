---
title: "New VNC install - 'cleanly exited too early'"
date: 2021-12-23
forum: General Help
---

### Post by Dev'olution on 2021-12-23
So I've installed tightvncserver, set up xfce, set up my vncstartup with the following:

```
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```

Except I get this:

```
kristian@alpha:~$ vncserver

New Xtigervnc server 'alpha:1 (kristian)' on port 5901 for display :1.
Use xtigervncviewer -SecurityTypes VncAuth -passwd /home/kristian/.vnc/passwd :1 to connect to the VNC server.

vncserver: Can't exec '/home/kristian/.vnc/xstartup': Permission denied

=================== tail /home/kristian/.vnc/alpha:5901.log ===================
Can't exec "/home/kristian/.vnc/xstartup": Permission denied at /usr/share/perl5/TigerVNC/Wrapper.pm line 1073.
===============================================================================

Session startup via '/home/kristian/.vnc/xstartup' exited with status 1!

Maybe try something simple first, e.g.,
        tigervncserver -xstartup /usr/bin/xterm
The X session exited with status 1!
Killing Xtigervnc process ID 7103... success!

```

Now I checked by using sudo vncserver if that would work, and yes, it creates a vncserver for root. 

So I chmod'd the file to 755 so my user could access it and now I get 

```
kristian@alpha:~$ vncserver

New Xtigervnc server 'alpha:3 (kristian)' on port 5903 for display :3.
Use xtigervncviewer -SecurityTypes VncAuth -passwd /home/kristian/.vnc/passwd :3 to connect to the VNC server.


=================== tail /home/kristian/.vnc/alpha:5903.log ===================
===============================================================================

Session startup via '/home/kristian/.vnc/xstartup' cleanly exited too early (< 3 seconds)!

Maybe try something simple first, e.g.,
        tigervncserver -xstartup /usr/bin/xterm
The X session cleanly exited!
Killing Xtigervnc process ID 9318... success!

```

Anyone able to help?

---

### Post by Dev'olution on 2021-12-23
Should also add, that i'm running 21.10

---

### Post by roblwe on 2022-03-15
Hello,

Just created an account, because I had the same problem and found the solution....

Your skript seems to be okay, except for the "&" after the: "startxfce4 &" line.

Solution: remove the "&", save and try to start the vncserver again by executing the command: "vncserver ( :Number of your VNC-Server ~normally its ":1")"


Might just be a bit late now, but maybe it'll help people in the future..

---

### Post by maemarcus on 2022-12-18
Indeed, removing "&" is the solution! But "&" was [mentioned in earlier tutorials]("https://www.reddit.com/r/regolithlinux/comments/hwbhjs/xstartup_for_vnc_to_run_regolith/"), and actually works in 20.04. So apparently the vncserver behavior has changed in 22.04.

Thank you very much for your kind willingness to help people!

---

