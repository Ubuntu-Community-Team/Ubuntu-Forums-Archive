---
title: "Tightvncserver only lets me log in once"
date: 2014-03-31
forum: General Help
---

### Post by Caleb_Crum_ on 2014-03-31
I'm using tightvncserver on ubuntu 13.10. I can start a new desktop and log in fine from tighvnc viewer on my laptop but if I close that session and try to open it again tightvnc tells me 'The server is not configured properly'. 

I checked the log and it seems like this is the problem

```


31/03/14 01:13:47 Got connection from client 74.*.*.*
31/03/14 01:13:47 Using protocol version 3.8
31/03/14 01:13:47 Enabling TightVNC protocol extensions
31/03/14 01:13:50 rfbVncAuthProcessResponse: could not get password from /home/caleb/.vnc/passwd
31/03/14 01:13:50 Client 74.*.*.* gone
31/03/14 01:13:50 Statistics:
31/03/14 01:13:50   framebuffer updates 0, rectangles 0, bytes 0
Error executing command as another user: Not authorized


This incident has been reported.


```

I'm not exactly good enough to come up with a solution to this so does any have any ideas?

---

