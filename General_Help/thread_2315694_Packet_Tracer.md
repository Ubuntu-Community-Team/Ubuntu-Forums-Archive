---
title: "Packet Tracer"
date: 2016-03-01
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-03-01
I have this file called Cisco Packet Tracer and I'm trying to install it in Ubuntu 15.10.  I know this a simple question, but everything is extracted now into my Documents folder and I don't know where to go from here installing it!

---

### Post by QDR06VV9 on 2016-03-01
Hey shane_faulkinbury2
This is from their site for a how to:
[http://askubuntu.com/questions/335785/how-do-i-run-cisco-packet-tracer-6-0-1](http://askubuntu.com/questions/335785/how-do-i-run-cisco-packet-tracer-6-0-1)
I had seen where you had post there..
EDIT: I guess some had problems running the program after installing it.
> Try setting execute permission to the PacketTracer6 file inside bin folder ( /opt/pt/bin )
I had the same issue , checked the file permissions and saw it wans't executable . For this you can try  running in terminal
chmod +x PacketTracer6
( when inside the /opt/pt/bin folder )


Hope this is helpful

---

