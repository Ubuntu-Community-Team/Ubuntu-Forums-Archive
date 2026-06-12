---
title: "help to set DISPLAY ?"
date: 2007-03-08
forum: General Help
---

### Post by zyx on 2007-03-08
Hello,

I have two computers that have kunbuto 6.06. when I use ssh to login a remote computer (kunbuto 6.06), but I cannot use X windows! The error message is as follows:

usr1@comp2:~$ xterm &
[1] 19801
usr1@comp2:~$ xterm Xt error: Can't open display:
xterm:  DISPLAY is not set

[1]+  Exit 1                  xterm
usr1@comp2:~$ export DISPLAY=comp1:0.0
usr1@comp2:~$ xterm &
[1] 19803
usr1@comp2:~$ xterm Xt error: Can't open display: comp1:0.0

[1]+  Exit 1                  xterm
usr1@comp2:~$ startx
xauth:  creating new authority file /u/usr1/.serverauth.19858

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

How to set DISPLAY? I can use X windows! Thanks!

---

### Post by Jussi Kukkonen on 2007-03-08
have you started ssh with the -X option (this can be done in your local *.ssh/config* too), and have you enabled this on the remote machine in */etc/ssh/sshd_config* using **X11Forwarding yes** (and have you restarted sshd after any changes)?

Oh, and by the way, you don't have to run the X server on the remote machine, just start the apps like you first tried. setting DISPLAY shouldn't be necessary either

---

### Post by zyx on 2007-03-08
Thanks for your reply!
I use 
ssh -X
it works well! thanks!

---

