---
title: "Vnc to computers on the net"
date: 2006-12-06
forum: General Help
---

### Post by CameronCalver on 2006-12-06
Hello i have a computer down the street for me and instead of going there i would like to remote desktop it and work on it ( both high speed internet) i no the ip from ip chicken but i do vncviewer then 203 ********** but it just hangs and does not do anything.
I have alos tried terminal server client but i am unsure of the things i have to fill in

---

### Post by bmt on 2006-12-07
> **CameronCalver said:**
> Hello i have a computer down the street for me and instead of going there i would like to remote desktop it and work on it ( both high speed internet) i no the ip from ip chicken but i do vncviewer then 203 ********** but it just hangs and does not do anything.
I have alos tried terminal server client but i am unsure of the things i have to fill in
A couple of things:

Have you set up the remote machine with a VNC server and is it running?

Is there a router/firewall on the remote machine's connection (probably)?  If so, it will need to have the vnc ports forwarded to the remote machine.

For more background information, Google for vnc (Real, Tight and Ultra are three likely flavours -- some are cross platform, but all have good information available).  Also, search for 'vnc' on these forums -- you're not alone!

---

### Post by dbott67 on 2006-12-07
As bmt mentioned, you may have issues with a router/firewall blocking port 5900.  Port 5900 must be forwarded to the internal IP address of the computer you wish to connect to.

Additionally, they may be running a software firewall that would block access.

Are they using Windows, Mac or Linux?  If you can provide as much detail as possible about the computers in question, we can walk you through it.

You can also try getting them to "[reverse VNC]("http://www.ubuntuforums.org/showthread.php?t=299489")" to your computer.  Check my signature for the details.

-Dave

---

### Post by CameronCalver on 2006-12-08
Ok it is linux to linux and the modem on the server is dg632

---

### Post by bmt on 2006-12-09
> **CameronCalver said:**
> Ok it is linux to linux and the modem on the server is dg632
Did you Google anything as I suggested above?

I'll get you started: [www.portforward.com/routers](www.portforward.com/routers)

---

