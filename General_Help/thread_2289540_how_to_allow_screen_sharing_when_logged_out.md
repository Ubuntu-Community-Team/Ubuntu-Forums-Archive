---
title: "how to allow screen sharing when logged out?"
date: 2015-08-04
forum: General Help
---

### Post by jacebennest on 2015-08-04
if i log out of my ubuntu machine, i can (and often do) ssh into it, and do what i need to do. sometimes, i want to be able screen share to get to the desktop. Normally if the ubuntu computer is just locked i can screen share no problem, but if i log out, it's a no go.

is there a way to login/launch the desktop environment via ssh, so i can then share screens?

---

### Post by TheFu on 2015-08-05
There are multiple ways. [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
Don't know about screen sharing - besides through tmux - and that is more like terminal sharing.

---

### Post by lukeiamyourfather on 2015-08-05
X2Go will create a new X session for the remote user that's not visible to local users so it doesn't matter if someone is logged in or not.

---

