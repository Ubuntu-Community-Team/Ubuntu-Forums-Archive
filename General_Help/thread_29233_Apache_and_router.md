---
title: "Apache and router"
date: 2005-04-23
forum: General Help
---

### Post by Lamber on 2005-04-23
Hi,

On my ubuntu machine I have Apache installed. When I go to 192.168.0.4 I can see my "website". 

On the machines in my network I can see the website, but i don't know how to set it up, so I can view it outside my network.

Situation:

modem (***.***.*.***) --> router (192.168.0.1, subnet 255.255.255.0)--> network (192.168.0.2, and *3, and *4)

Apache:

Apache/2.0.50 (Ubuntu) Server at 192.168.0.4 Port 80

Do I have to open certain ports on my router? 

Many thanks,

Lamber

---

### Post by localzuk on 2005-04-23
You need to set up port forwarding on your router. It is sometimes called Port Mapping. Example:

Source Address: ***.***.***.***
Source Port: 80
Destination Address: 192.168.0.4
Destination Port: 80

This should point all port 80 traffic to your web server.

---

### Post by Lamber on 2005-04-24
[QUOTE=localzuk]You need to set up port forwarding on your router. It is sometimes called Port Mapping. Example:

Source Address: ***.***.***.***
Source Port: 80
Destination Address: 192.168.0.4
Destination Port: 80

This should point all port 80 traffic to your web server.[/QUOTE]

I thought it had something to do with my Apache settings :P

I've opened the port on my router and modem, and it still wont work :(

modem:

Source: **.***.*.***
Port: 80 
Destination: 192.168.0.4
Service: tcp

router:

same as above

When I connect to 192.168.0.4 and 10.0.0.150 it works, i can see my site. But when I try to connect to my ip it doesnt work (also have a .tk domain, who redirects to my ip).

---

