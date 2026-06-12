---
title: "x11vnc exit's gracefully not so graceful"
date: 2013-08-04
forum: General Help
---

### Post by jcllings on 2013-08-04
I have x11vnc configured to startup automatically on restart and present the login screen.   Problem is that after a period of unconnected inactivlty my laptop shuts me out. When I try to reconnect I get a message like "Connection close gracefully" and then I have to find a way to get in to this headless laptop.  Usually this entails digging in to it's relatively inaccessible location, dragging it out and opening it. Molest it a bit till it displays the lock screen, shut it and put it back, go back to my desk and log in. 

A major pain in the aft quadrant, if you know what I mean, and  a general deterant to using my Linux laptop.  

1. Is there something I can do to get around this?
2. If not, is there a way using something besides x11vnc even on another distro as I find this situation utterly intolerable.

---

### Post by jcllings on 2013-08-16
Anybody? Buler.... Buler.... We'll come back to Buler...

---

### Post by jcllings on 2013-11-23
Solved by using synergy over an autossh connection instead. It's a lower bandwidth solution.

---

