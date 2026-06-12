---
title: "VNC resumable login fails on Hardy 8.04"
date: 2008-05-22
forum: General Help
---

### Post by oregonbob on 2008-05-22
I had VNCserver running great on 7.10 using /etc/inetd.conf entries to start Xvnc, but after an upgrade to 8.04 I cannot get vncserver to run. It logs "...can't get client address: Transport endpoint is not connected...".

Has anyone got multiple resumable sessions of VNC running on 8.04? There is a tutorial here, [http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036), but I could not get this working either. The standard :0 works OK, but I want user to be able to get a GDM login screen, login and then start a vnc gnome session. This worked great on 7.10. I previously had 4 screens enabled for vnc :1, :2, :3...

---

### Post by rh10023 on 2008-07-28
oregonbob, I am running into the same problem and same error message.  Just was curious if you found any solutions to it?

---

