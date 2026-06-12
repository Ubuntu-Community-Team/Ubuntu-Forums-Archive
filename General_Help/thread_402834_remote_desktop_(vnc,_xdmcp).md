---
title: "remote desktop (vnc, xdmcp)"
date: 2007-04-06
forum: General Help
---

### Post by loveshocked on 2007-04-06
Hi all, 

i am a new ubuntu user.
 I am still trying to figure out about the remote desktop. I was wondering whether there is a remote desktop based installation than allow a lot of user to login in a same time (sort of like windows server, where there are USERS, that can login in a same time)
hopefully, this software is capable of doing a remote desktop from windows as the clients.

I tried vnc once, but it is just for one user at the same time, and xdmcp, which is not ready to be remoted from windows. I am using ubuntu edgy.



Thanx for the infos :-D

---

### Post by Origin415 on 2007-04-06
I havent personally used it before, but this might be what you are looking for:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Remote_Desktop_Access_via_NX](http://ubuntuguide.org/wiki/Ubuntu_dapper#Remote_Desktop_Access_via_NX)

Good luck.

---

### Post by jeffathehutt on 2007-04-06
NX is the way to go.  It does everything you wanted, plus it is very easy to set up.

---

### Post by SendDerek on 2007-04-06
I think I may know what it is your looking for.  I was searching myself for this solution and I didn't want to go through the extra trouble to setup NX.

Just install xnest by using 

> sudo apt-get install xnest

And then goto Applications->Internet->Terminal Server Client and then choose "xdmcp" as the connection protocol and connect to the remote computer.  It works just like Window's RDP.  Although, I'm not sure how to set it up for multiple users.  I've only tried connecting one user at a time in my home environment.

---

