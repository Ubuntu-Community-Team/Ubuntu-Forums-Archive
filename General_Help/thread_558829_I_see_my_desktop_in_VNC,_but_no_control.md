---
title: "I see my desktop in VNC, but no control"
date: 2007-09-24
forum: General Help
---

### Post by bullish on 2007-09-24
Hi,

I am trying to connect to my open gnome session on my ubuntu box from the lab (I don't want to start a new session). So I have enabled remote desktop, and checked allow control, and enable password.

So I go to the lab, on a windows box with realvnc, start up vncviewer and type 'ubuntuhostname' and a password dialog pops up. I enter the password, and can see the desktop, the mouse is reflected, but no keyboard or mouse clicks are detected. Is there a setting I missed because it does not appear I have control of the machine.

Thanks!

---

### Post by bullish on 2007-09-24
I made a new observation. It looks like mouse and keyboard events from the vncclient are being passed to the server. I tried to type some characters, but they didn't show up on the client display. When I walked back to my 'server' machine, the characters from the client machine actually made it through. They just were not being reflected back to the client. It is as if I am staring at a snapshot of of the screen, but the server does not respond back.

---

