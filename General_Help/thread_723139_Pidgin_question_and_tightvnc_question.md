---
title: "Pidgin question and tightvnc question"
date: 2008-03-13
forum: General Help
---

### Post by BrutusB on 2008-03-13
Pidgin - how can I make it startup when I log in?

tightvncserver - how can I make this service available before I log into the system?  I am forced to login to my machine before I am able to connect via vnc

---

### Post by NorthernLights on 2008-03-13
Pidgin: in Preferences -> Sessions (something like that, i'm at work under Windows right now), you can add commands to be started with Gnome

tightvncserver : edit /etc/rc.local as root ("sudo gedit /etc/rc.local" for instance) and add the command to start tightvncserver before "exit 0". I think the command is as simple as "tightvncserver&".

---

### Post by Redenbacher on 2008-03-13
> Pidgin - how can I make it startup when I log in?

In Preferences -> Sessions (Just as Northern Lights said) you're going to add a new program to the list. For command, you're going to enter pidgin, just as you would in terminal. Then save it, and the next time you log in pidgin should start up.

 If that does not work, log in, start up pidgin and whatever other apps you want running on start up, but ONLY those apps. Go in to sessions again, click the last tab and hit "Save Current Session." This will save all apps that are currently running in to a session and start it up the next time you log in!

Hope that helps!

---

### Post by BrutusB on 2008-03-14
Thanks!  I got Pidgin going on startup.  I still can't seem to get tightvnc going without logging in.  I made that file edit above.  Do I include the & at the end?

---

