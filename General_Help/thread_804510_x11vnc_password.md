---
title: "x11vnc password"
date: 2008-05-23
forum: General Help
---

### Post by Trollslayer on 2008-05-23
With 8.04 (using Mythbuntu) x11vnc starts up automatically but I can't get it to accept the password.
I've tried vncpasswd and x11vnc -storepasswd in user and su modes, any suggestions?
Alternatively, I've looked for where x11vnc starts up so I can add -rfbauth to the file of my choice. Where would I find it or what would be an easy way to earch (new to searching in Linux).
Ta.

---

### Post by krunge on 2008-05-23
> **Trollslayer said:**
> With 8.04 (using Mythbuntu) x11vnc starts up automatically but I can't get it to accept the password.
I've tried vncpasswd and x11vnc -storepasswd in user and su modes, any suggestions?
Alternatively, I've looked for where x11vnc starts up so I can add -rfbauth to the file of my choice. Where would I find it or what would be an easy way to earch (new to searching in Linux).
Ta.

Maybe try "grep -r x11vnc /usr"  This may take a long time and spit out lots of "Permission denied", etc.  Change "/usr" to other dirs, e.g. "/etc" or even "/" if they show nothing.  Before that try "locate x11vnc" or "find / -name '*x11vnc*'" or see if you have something that is like spotlight enabled (beagle?)

---

### Post by Trollslayer on 2008-05-23
> **krunge said:**
> Maybe try "grep -r x11vnc /usr"  This may take a long time and spit out lots of "Permission denied", etc.  Change "/usr" to other dirs, e.g. "/etc" or even "/" if they show nothing.  Before that try "locate x11vnc" or "find / -name '*x11vnc*'" or see if you have something that is like spotlight enabled (beagle?)

Thanks, I found what I needed with that help (it was in a Mythbuntu startup script).

:KS

---

### Post by krunge on 2008-05-24
> **Trollslayer said:**
> Thanks, I found what I needed with that help (it was in a Mythbuntu startup script).

:KS

For reference, what is the full path to the file that does it?

---

### Post by maxim99 on 2008-07-07
/usr/share/mythbuntu/session.sh

Near the end of the script.

I actually had issues with functionality afterwards. Not resure why the command didn't work when I ran it from the command line. Maybe it works different when the system is initially start up and the session.sh is run by Init instead. Who knows. Ultimately I changed the command line to this:

x11vnc -rfbauth /root/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -auth /var/lib/gdm/:0.Xauth

And it allowed me to start up the vnc server from the command line, and I'll imagine that it'll start fine just as well when the system starts up on it's own.

The only changes I made were adding the auth switch which allowed it to connect to the X11 display that was already running.

---

