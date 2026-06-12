---
title: "RDP client comparable with Remote Desktop on XP?"
date: 2008-02-06
forum: General Help
---

### Post by Fafnr on 2008-02-06
Hey all,

Is there some RDP client for Linux that allows file transfers like Remote Desktop for Win XP?
See, having access to *use* the computer is fine - but I need to be able to transfer files as well.
As I have no control over the other computer (it's a server hosting our economy-system), I can't setup FTP / SSH / SCP, and the company hosting refuses to do so for us. 

Normally, I'd just use XP, but for some reason neither my Laptop NOR my Desktop can connect to the server, though I've tried everything, and from different networks.

I've tried rdesktop (well, grdesktop...) and whatever built-in client Ubuntu has, but I can't seem to find anything about mounting my own filesystem so I can transfer files...

I really hope someone knows?

Regards,

Søren G. Andersen

---

### Post by perfecttao on 2008-02-06
For windows, there is UltraVNC, which supports file transfer, but there is no linux port, that I know of.

If you don't have any joy though, there is a slightly convoluted approach.

If the server you are connecting to has outboung http or FTP access, you could host an FTP/HTTP server at your site and initiate the connection using your RDP session on the remote machine??  Slightly long winded, I know, but I've used ths approach in the past for servers that I only have access to "remote control" but not transfer files to....

---

### Post by Fafnr on 2008-02-06
Actually, that FTP-thing isn't a bad idea...
Unfortunately, I don't have many privileges on the machine. I can install a program to the drive I have access to, but it doesn't show up in start / programs...

I know this is probably beyond the scope of the Ubuntu forums, but do you know a very lightweight FTP server that I could (probably) run in such a scenario? It doesn't have to be flashy or fancy in ANY way!

Thanks again in advance!

Regards,

Søren Andersen

---

### Post by perfecttao on 2008-02-06
vsftpd - it's fast, secure and free and in the Ubuntu repo's.

As for the client on the remote machine, you can either use Internet Explorer, or if you have Firefox, the FireFTP plugin is pretty good - that is, if you don't want to use the built in FTP client on the command line.

Good luck

---

