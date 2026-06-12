---
title: "gksu nautilus and gedit problem"
date: 2007-02-10
forum: General Help
---

### Post by mnunez on 2007-02-10
Whenever I use terminal to open nautilus or gedit, I get these messages.   Any idea what there error mean?  Thanks in advance.
--------------------------------------------------------------------------------------
torrent@PIII800:~$ gksudo nautilus

(nautilus:15208): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:15208): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
torrent@PIII800:~$ 
--------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------
torrent@PIII800:~$ gksu gedit

(gedit:15696): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
torrent@PIII800:~$ 
_____________________________________________________________________

---

### Post by meng on 2007-02-10
The first part of the warning
(Gnome-UI-WARNING: etc.)
is normal and can be ignored.

IIRC, the second part is normal too when running nautilus.

---

