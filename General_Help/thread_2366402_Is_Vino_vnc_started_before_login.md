---
title: "Is Vino vnc started before login?"
date: 2017-07-17
forum: General Help
---

### Post by henkman on 2017-07-17
Hi, I was wondering if the default vino vnc server already runs before login. ( I am running ubuntu 16.04.2) I ask this because I can only use xrdp remote login when I am already logged on to the machine. I believe because vino does not have started before login but want to verify this..
Generally.. how can I find out which processes have started before login?

Regard, 
Henk

---

### Post by kensuaga on 2017-08-22
Did you find an answer to this? I have been looking for a long time now. I even tried to add it to the start up applications.

---

### Post by sp40140 on 2017-08-22
No. It doesn't (by default).
However, there are scripts out there on internet which you can add and configure to run it before log-in. However, use common sense and caution when pulling any scripts from internet.

---

### Post by jefelex on 2017-09-11
I also have this exact same problem - I have a server that I can log in to with ssh no problem, I can also log into it with vnc (remmina) when there is a user logged into gnome on the server. What I am trying to do is to activate the gnome environment from my remote ssh session when no one is logged into the server.  I can log into the server with my username when no one is logged in, but what I am trying to do is log into a gnome desktop session from my ssh terminal screen on my personal (client) machine.  I have searched and searched for a solution, but come up with a bunch of ineffective solutions.  I have tried Xvfb and export DESKTOP=:0, also Xterm can run graphic apps on the server, but what I really want to do is have the graphic login screen from the server (preferably with my remmina client) so I can log into the graphic session on the server.  The whole reason for this is to mount my USB drives that are mounted by gnome when it is started.  They will not mount until a user logs into the graphic session on the server.  I hope I have been able to explain what I am trying to say!! :)

---

