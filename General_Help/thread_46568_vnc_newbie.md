---
title: "vnc newbie"
date: 2005-07-05
forum: General Help
---

### Post by shizow on 2005-07-05
i try to connect at home from my laptop to my desktop rechner

on both i have ubuntu
i started vnc4server on the desktop
then i try to connect with my laptop with
xvnc4viewer to the ip of my desktop
but i get a connection refused

can anyone help

---

### Post by IchBin on 2005-07-05
[QUOTE=shizow]i try to connect at home from my laptop to my desktop rechner

on both i have ubuntu
i started vnc4server on the desktop
then i try to connect with my laptop with
xvnc4viewer to the ip of my desktop
but i get a connection refused

can anyone help[/QUOTE]
 You'll need to make sure you have the proper port forwarded in your firewall.  Also the router if you're accessing it through your outside IP. 

[http://www.realvnc.com/faq.html#firewall](http://www.realvnc.com/faq.html#firewall)

---

### Post by shizow on 2005-07-05
[QUOTE=IchBin]You'll need to make sure you have the proper port forwarded in your firewall.  Also the router if you're accessing it through your outside IP. 

[http://www.realvnc.com/faq.html#firewall](http://www.realvnc.com/faq.html#firewall)[/QUOTE]

but i am inside my home lan, i am not connecting over the internet

---

### Post by IchBin on 2005-07-05
That still doesn't stop your firewall from blocking you.

---

### Post by shizow on 2005-07-05
[QUOTE=IchBin]That still doesn't stop your firewall from blocking you.[/QUOTE]

thanks now i can connect
but i only get a grey window with an x as mouse pointer

---

