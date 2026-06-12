---
title: "Can I Remote Desktop Into Ubuntu Box?"
date: 2007-05-26
forum: General Help
---

### Post by klgsx on 2007-05-26
I configure an Ubuntu desktop for basic printer and fire-sharing.   Is it possible to "Remote-Desktop" into the machine ala "windows xp"??

I will be remote connecting from a windows xp.. so here are my questions:

1)  What do i need to do to allow "full control of the box"

2)  What windows software do can I use or can i use the building-remote desktop software that come with windows xp?

Any Detail Suggestion is Welcome!

Thanks

---

### Post by Richard Kut on 2007-05-27
Select System --> Preferences --> Remote Desktop from the menu bar. Place a tick in the box next to the option "Allow other users to view your desktop", and then close this applet. This will start a VNC server on your Ubuntu machine. Now download and install a VNC client (viewer) on your Windows box. Then, from the Windows box type the command vncviewer ubuntu:0, assuming here that your Ubuntu machine is actually named ubuntu. Substitute the correct name for your setup. Please update this post with your feedback. Good luck!

---

