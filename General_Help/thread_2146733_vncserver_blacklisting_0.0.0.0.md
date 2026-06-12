---
title: "vncserver blacklisting 0.0.0.0"
date: 2013-05-19
forum: General Help
---

### Post by jonsparks on 2013-05-19
Hi all,
I'm running a vnc4server install on Ubuntu 12.10. Every time I need to access my VNC server, I have to restart it because I get a "Too many security failures" error. I've tried accessing my VNC server from multiple locations and that hasn't helped. Today, I looked at my log and saw that 0.0.0.0 has been blacklisted. I assume this would be the cause of it, but I don't know how to prevent it from getting automatically blacklisted. 

Here's the text from the vncserver log.

Sun May 19 14:30:49 2013
 SConnection: AuthFailureException: Authentication failure
 Connections: closed: 0.0.0.0::51802 (Authentication failure)

Sun May 19 14:35:29 2013
 Connections: blacklisted: 0.0.0.0

Sun May 19 14:35:51 2013
 Connections: blacklisted: 0.0.0.0

Sun May 19 14:37:30 2013
 Connections: blacklisted: 0.0.0.0

---

