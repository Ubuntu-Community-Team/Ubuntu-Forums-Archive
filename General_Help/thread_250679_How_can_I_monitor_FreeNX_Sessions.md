---
title: "How can I monitor FreeNX Sessions?"
date: 2006-09-04
forum: General Help
---

### Post by zhenya on 2006-09-04
I've recently started using FreeNX for remote gui access to my Dapper server.  Very impressive!  Compared to VNC over SSH which was almost unusable over anything but a fairly local, fast connection, FreeNX is running superbly for me over a slow, high latency satellite connection from the opposite side of the world!  

Anyhow.  One aspect of VNC that I like is that I can easily determine running sessions from the command line via the 'who' command.  FreeNX sessions don't show up anywhere though.  I like to maintain a high level of knowledge as to what's going on on my servers, but I can't yet figure out how to monitor existing FreeNX connections.  Does anyone know how to do this?  TIA!

---

### Post by master_b on 2006-09-06
NX Session Administrator (GUI) should have been installed along with NX,

Check under Internet on your Menu ( I'm using KDE/Kubuntu so it may be elsewhere under Gnome)

Bill

---

### Post by zhenya on 2006-09-07
I have a session administrator under my windows client, but I can't find anything similar on the server.  It really seems like there must be a way to monitor this via an ssh shell...

I mean, I can trace the logins in auth.log, but that's a pretty backhanded way to have to monitor what's going on.  

I have to be missing something here.  I'm confused as to why the user session doesn't show up in the usual places.  As I understand it, NX creates the initial connection to a very limited shell with the user NX.  It then authorizes the normal user through that limited shell.  If that's so, then why doesn't the shell report when an NX user is logged in?  

Anyone?

---

