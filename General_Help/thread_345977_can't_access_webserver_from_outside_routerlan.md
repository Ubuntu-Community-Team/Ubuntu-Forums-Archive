---
title: "can't access webserver from outside router/lan"
date: 2007-01-25
forum: General Help
---

### Post by tr333 on 2007-01-25
I have an apache webserver running on ubuntu sever setup on a LAN behind a netgear router.  I also have a dyndns address setup for connecting to the dynamic IP from outside the LAN.  When trying to access the webserver, I can access it from any machine on the LAN using both the LAN ip address and the dyndns address.  When I try to access it from outside the LAN, it gets a timeout error.  I've tried looking at the router config for port forwarding but I can't see any problem with this as I can login remotely to the machine from outside the LAN using ssh.  I'm also not sure if the router is supposed to respond to Ping requests, as I can't seem to be able to ping the router from any machine outside the LAN.

I'm not sure if this is actually a router config problem or if it's something wrong with my ubuntu/apache install.


EDIT:  I just realised i had the router set to ignore ping requests.  still having the other problems though..  i should also mention that my router is a Netgear FVS318v3 incase there's specific problems with netgear :s

---

### Post by tr333 on 2007-01-26
i've just tested apache on port 81, and it seems to be working fine with the router successfully redirecting all port 81 access to my server.  still  no idea why it is getting blocked on port 80, since i have no rules setup in iptables.

---

### Post by distortedstar on 2007-02-21
I'm having a similar prob...set up an apache web server on my home box, with a dyndns address (distortesdstar.homelinux.net) and I can of course access it from the machine itself...but it doens't work from a remote location. Not sure how to configure ports and stuff yet. Any help would be appreciated.

---

### Post by tr333 on 2007-02-21
my problem was with the ISP blocking port 80.  you can change the listening port of apache by editing the file /etc/apache2/ports.conf

---

### Post by distortedstar on 2007-02-21
Yes, it was my ISP blocking the port. Thanks for the workaround idea!

---

### Post by stickmangumby on 2007-02-22
Often ISPs also let you unblock the ports they block by default (like http, telnet, smtp etc) in your online preferences or settings or toolbox. Having apache set to port 81 is a bit of a pain for people who will access your site apart from you!

---

### Post by tr333 on 2007-02-22
i changed my webserver to operate from port 8080 since that is the designated "HTTP Alternate" port. [http://www.iana.org/assignments/port-numbers]("http://www.iana.org/assignments/port-numbers")

---

