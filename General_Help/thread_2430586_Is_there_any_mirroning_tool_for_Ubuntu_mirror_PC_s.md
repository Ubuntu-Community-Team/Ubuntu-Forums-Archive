---
title: "Is there any mirroning tool for Ubuntu mirror PC screen to iPhone, without remote fun"
date: 2019-11-04
forum: General Help
---

### Post by jasper99 on 2019-11-04
tion? and log out at serveral minites of inactivity.

Only want to see the PC screen on iPone, no remote.
It also not must have any icon on the PC screen, on the iPone screen it is not a bog problem.

---

### Post by HermanAB on 2019-11-05
Hmm, I think the tool is called a MacBook.

---

### Post by saymyname2 on 2019-11-05
What you want is a VNC viewer.

when you generate a new VNC session for the first time you will be asked to set up a password and and the second question if this is only for viewing. Just answer this questio with yes.

then you start as user the vnc session

vncserver -geometry 1900x1200 :1

and on your ipad install VNC Viewer and connect to the port of the host: HOSTIP:5901

---

### Post by jasper99 on 2019-11-06
Not tried but VNC is with remote, only search for App see the screen, so don't turn my PC screen on every time.

---

### Post by saymyname2 on 2019-11-06
With VNC you don't need any screen on your PC.

You just want the iPad show the Desktop, right without controlling. Or what is it exactly?

---

### Post by HermanAB on 2019-11-07
You should also look at tmux and xpra.  Both are more light weight than VNC. 
[https://www.redhat.com/sysadmin/ssh-tmux-screen-sharing](https://www.redhat.com/sysadmin/ssh-tmux-screen-sharing)
[http://xpra.org/](http://xpra.org/)

---

