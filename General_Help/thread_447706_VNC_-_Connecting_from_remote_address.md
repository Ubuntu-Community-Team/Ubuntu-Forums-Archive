---
title: "VNC - Connecting from remote address"
date: 2007-05-18
forum: General Help
---

### Post by linuxbun on 2007-05-18
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

When I try this locally (using it's local ip addy) it works fine.

(Though, I might add it's using the command:
[B]
vncviewer -via bunny@192.168.0.102 bunny:[/B]    & not
**vncviewer -via bunny@192.168.0.102 bunny:1** as indicated to do.  
                  For some reason, putting a number at the end just gives me a grey screen)

However, when I try this remotely (from my friends house) using the external ip address, it simply times out and doesn't connect. The computer that I want to connect to is connect through a Netgear Router which I believe has a firewall. Do I have to forward some ports to make it work? 

I'm still a bit unsure how. Any pointers would be most appreciated.

---

### Post by thelinuxguy on 2007-05-18
VNC uses port 5900. Maybe this port is not forwarded on the router. And besides, iptables may be blocking the incoming connections.
Try this first and see if you can connect.
```

sudo iptables --flush

```
If it does, then instead of flushing all the rules, you may want to create a rule for allowing the VNC connection. I haven't done this myself so maybe someone could post how to do this or you can have a look at some iptables reference.

If not, check the port forwarding on your router.

> 
vncviewer -via bunny@192.168.0.102 bunny:1 

Try putting a 0 at the end to connect to display number 0.

---

### Post by fanatik on 2007-05-18
using a netgear router you would need to use the web interface to port forward port 5900 to the ip address that vncserver is running on. point your browser to [http://192.168.0.1/](http://192.168.0.1/) or whatever the ip of your router is (that is what it was on my old netgear) and select port forwarding from the menu on the left. i don't know about newer routers, but i remember the help was very good, check your routers manual for more info.

---

### Post by linuxbun on 2007-05-18
Ahhh gotcha. Just forwarded a port and I'll test shortly!!

---

