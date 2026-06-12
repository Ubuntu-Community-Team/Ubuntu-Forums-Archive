---
title: "Edubuntu Viewed from Ubuntu??"
date: 2007-04-26
forum: General Help
---

### Post by becatlibra on 2007-04-26
I installed Edubuntu (edgy)on my son's PC (a desktop install, not as a thin client) - I thought I would still be able to view his sessions and kill applications (using thin client manager - I have ubuntu fiesty)

I tried installing x11vnc and then

"Now edit the rc.local file to add x11vnc to the system startup

vi /etc/rc.local

Add the following line before the exit 0 statement in this file and save it:

x11vnc -display :6 -forever -bg"

Didn't work

Is this impossible? Am I missing something?

Thanks

I tried posting this somewhere else but it seems to have been overlooked. . .

Benjamin

---

### Post by Tomosaur on 2007-04-26
Make sure you enable the remote stuff on both machines. Your sons machine needs to be setup to accept remote sessions, and your machine needs to be setup to connect to a remote machine.

---

