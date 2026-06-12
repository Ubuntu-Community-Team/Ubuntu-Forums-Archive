---
title: "vnc remote desktop"
date: 2013-07-02
forum: General Help
---

### Post by MikeCyber on 2013-07-02
HI
my old pc has 12.10 and my new 13.04. I enabled with vino-preferences guests but cannot access from 13.04 with Remmina. What could I be doing wrong?
Thanks

---

### Post by TheFu on 2013-07-02
There are hundreds of possible answers.

Can each machine ping the other by IP?  By name?

Can each machine ssh into the other ... is ssh-server installed on both sides?  I prefer to use ssh over VNC most of the time, though it isn't directly relevant to your question.  ssh-key-based authentication rocks completely.

Did you start the VNC server and setup the startup environment as you like?

What do the log files show?  Often, those tell us everything we need to know. May need to turn up the logging levels.

---

### Post by MikeCyber on 2013-07-02
Hi
Ping works, also samba to get my files to the new pc.
I didn't try ssh. As for vnc I only fired up the vino-preferences nothing else and allowed guests. Vino seems to be running with ps aux but 
I cannot access it from 13.04.
Thanks

---

### Post by TheFu on 2013-07-02
> **MikeCyber said:**
> Hi
Ping works, also samba to get my files to the new pc.
I didn't try ssh. As for vnc I only fired up the vino-preferences nothing else and allowed guests. Vino seems to be running with ps aux but 
I cannot access it from 13.04.
Thanks

I've never used vino or rem.... I'm a pure vncserver and vncviewer guy.

If you start the server from the terminal and turn up the verbosity, perhaps you can see errors when a client connection is attempted?

Did you find and look at the log files? Those are your best bet now.

Might be worth reading through this: [http://ubuntuforums.org/archive/index.php/t-1335744.html](http://ubuntuforums.org/archive/index.php/t-1335744.html)  to see about security for VNC.

---

