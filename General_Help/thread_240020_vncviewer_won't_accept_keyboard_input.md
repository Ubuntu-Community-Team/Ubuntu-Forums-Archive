---
title: "vncviewer won't accept keyboard input"
date: 2006-08-20
forum: General Help
---

### Post by compwiz18 on 2006-08-20
When I start vncviewer from the command line, type in my password, and connect, it all works fine until I make it fullscreen.  When I make it fullscreen, the keyboard input is no longer directed into the viewer, instead it is directed into the terminal that VNC is running in.  If I start it with the -fullscreen switch, it works fine, unless I unfullscreen it and then fullscreen it again...

Any ideas?  thank you.

---

### Post by ProjectGod on 2006-08-21
not really a solution to this glitch but i like to make a shortcut of nifty little apps onto my desktop. let us know how you go when there's no terminal to begin with.

---

### Post by compwiz18 on 2006-08-21
I would try that, but I have to have a terminal open to input my password...I looked to see if there was command line option in which I could specify my password, but I didn't see one.

---

### Post by ProjectGod on 2006-08-21
no not really. you can create a shortcut on your desktop for the target **/usr/bin/vncviewer** and just double click on it to enter the VNC server and password.

see attached.

---

### Post by h00s on 2006-08-21
Install vnc4 viewer (sudo apt-get install xvnc4viewer).
It's a newer version, maybe it will work better ;-)

---

### Post by braddcadd on 2008-07-12
I had the exact same problem in Hardy.  Installing xvnc4viewer worked for me.

Thanks

---

