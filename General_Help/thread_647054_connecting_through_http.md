---
title: "connecting through http"
date: 2007-12-21
forum: General Help
---

### Post by laxwrestler on 2007-12-21
hey, i'm trying to use my desktop as a server.  I'm having trouble connecting to it through http.  ive set up ftp and ssh and can connect fine using those but if i try to connect to [http://(my](http://(my) ip address) it just says cant establish a connection.  This only occurs if i am trying to connect from outside my network.  Inside my network it works great but over the internet...nothing.  my desktop is behind a modem and a router but both have port forwarding set up for port 80.  if anyone could help it would be greatly appreciated.

---

### Post by p_quarles on 2007-12-21
Most likely your ISP has port 80 blocked from outside your network. There's little you can do about that, but you can always configure the web server to use an alternate port.

---

### Post by laxwrestler on 2007-12-21
well that sucks, anyone know how i would configure it to go through a different port?

---

### Post by p_quarles on 2007-12-21
Here's a tutorial on setting up a web server:
[http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

Toward the end, he gives instructions on setting up an alternate port, with full DNS support. Basically, it consists of two things: 1) Changing the /etc/apache2/ports.conf to "Listen 8080"; 2) Configuring your DNS server automatically forward http requests to that port.

---

### Post by laxwrestler on 2007-12-22
well port 8080 doesnt seem to be working either, anyone know if my isp could be blocking that port also? im on verizon and im pretter sure its agaisnt there tos to set up a server whether for personal or commercial use so maybe they are blocking ports generally used for http?.  once again it works over port 8080 inside my network but not over the internet.  i'm fairly certain ive set up port forwarding correctly also.

---

### Post by p_quarles on 2007-12-22
Try 8090? If that fails, you can always try a high port, like 45983 or something. It's very doubtful they're blocking those.

---

### Post by laxwrestler on 2007-12-22
well 45983 works over the network once again but not the internet :(.  so i suppose im setting something up wrong somehow or verizon has somehow managed to block any port using http.  i'll keep working on it. thanks for all the help man.

---

### Post by pyronaut on 2007-12-22
how about your firewall?? is that blocking connections. Or if you are using a router check the router ...in mine i have to set up a staitc ip to open up specific ports

---

### Post by ~LoKe on 2007-12-22
Why on earth would an ISP block port 80 and 8080?  Check your firewall settings on your router/IPtables.

---

### Post by p_quarles on 2007-12-22
> **~LoKe said:**
> Why on earth would an ISP block port 80 and 8080?  Check your firewall settings on your router/IPtables.
To prevent customers from running web sites from home. Was that a serious question?

To check firewall settings, you can run this command:
```
sudo iptables -L -v
```
Post the output here if you need help interpreting it.

---

### Post by laxwrestler on 2007-12-22
ok well i am a complete moron.  i had my firewall set up for 80 at first of course but when i changed the port i completely forgot about the firewall.  so yes verizon blocks port 80 (bastards) but they dont block 8080.  thanks for reminding me about the firewall guys. :)

---

