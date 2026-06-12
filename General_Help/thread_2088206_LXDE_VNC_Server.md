---
title: "LXDE VNC Server"
date: 2012-11-25
forum: General Help
---

### Post by M1GEO on 2012-11-25
Hello all.

I am trying to get a VNC server to run inside LXDE on Ubuntu Server.  I use some software on the server which I run under wine, but every attempt to start a VNC server on the current X session seems to start a new X session, no matter what I do. 

Just not sure what to do.  I just want to be able to see the screen on the server; X/LXDE is running on the the server all the time.

Any advice would be well received.

George.

---

### Post by M1GEO on 2012-11-25
Sorry to waste anyone's time.

It turns out that the program x11vnc will do exactly this.

"I must learn to use Google..."
"I must learn to use Google..."
"I must learn to use Google..."  :)

---

### Post by personalpc on 2012-11-25
how about using secure shell with x forwarding? 

ssh -c -X name@host

Make sure X is running on your client. Windows there is Xming and putty work great.

Once you connect with ssh just launch any application from the terminal and it will forward to the client pc's X display. Cheers!

[http://sourceforge.net/projects/xming/]("http://sourceforge.net/projects/xming/")

---

