---
title: "Can't open display - X tcp connection issue"
date: 2005-10-19
forum: General Help
---

### Post by tepegoz on 2005-10-19
Hi all,
I am using solaris machines, and transfer gui to ubuntu box.  I am not using any ssh staff.  I do "xhost +machine_name" on the ubuntu box, and then connect to the solaris, and do "setenv DISPLAY ip:0".  But solaris cannot open X connection.
The problem is this: Xwindows on ubuntu box does not listen tcp packets.
In hoary, I had changed the property of listen tcp connections from gnome_session properties (as I remember).  But it is not there in breezy. 

I also checked allow_tcp_connections in gconf, but it does not work.

Anyone know the solution?
Thanks in advance.

---

