---
title: "need help setting up remote desktop"
date: 2008-05-23
forum: General Help
---

### Post by demiurgen on 2008-05-23
i have a machine with ubuntu 8 desktop installed and set up ssh and enabled remote desktop.
then i have a mac with vncviewer.

when i start up my ubuntu machine with a monitor, remote desktop with vncviewer works perfect.
but when i start it up without a monitor plugged in, i get connection refused.

when i have started the ubuntu machine without a monitor, if i then plug in a monitor there is a message on the screen that says that ubuntu can't find my montor and that it will have to run in low-graphics mode.


anyone know how i can solve this so that i can use my ubuntu box without a monitor??

(ssh and my shared folders all work without a monitor)

---

### Post by barnex on 2008-05-23
An alternative to remote desktop is using ssh with X-forwarding. I've used this for a while on a mac. Make sure you have X11.app installed on your mac, then open /Applications/Utilities/X11, fire up an XTerm (cmd-N) and type: ```
ssh -YC username@machine
``` with your own username and machine. after entering your password, type: ```
gnome-session
``` to get to your Ubuntu desktop. Alternatively, use ```
gnome-panel
``` or just type the name of the application you wish to run. It's not the same as remote desktop, but personally I like this way of working.

---

