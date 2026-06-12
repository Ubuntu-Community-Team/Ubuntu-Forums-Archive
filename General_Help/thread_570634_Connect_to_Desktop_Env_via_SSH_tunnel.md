---
title: "Connect to Desktop Env via SSH tunnel"
date: 2007-10-08
forum: General Help
---

### Post by isolve on 2007-10-08
Hello,
I am trying to figure out how to connect to the Ubuntu desktop env as a second user.

I entered vncserver :1 in SSH session and connect to 5901 via vncviewer. However,  the vncviewer only shows the SSH session, but no the desktop env.


I tried to startx in the ssh session and saw the following error.

Please help.


root@u1688-desktop:/home/wz3n9v# startx
xauth:  creating new authority file /root/.serverauth.8694

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.
root@u1688-desktop:/home/wz3n9v# exit
exit
wz3n9v@u1688-desktop:~$ startx
xauth:  creating new authority file /home/wz3n9v/.serverauth.8719

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.
Couldnt get a file descriptor referring to the console

---

