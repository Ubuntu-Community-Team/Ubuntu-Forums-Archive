---
title: "How do I forward ports in Linux?"
date: 2013-03-28
forum: General Help
---

### Post by caleb12134 on 2013-03-28
I got the panel installed and it worked. but then i had to shut it down (long story) when it got back up i got this..... what does it mean and how do i solve it. how do i give this panel ports 2011 and 2012????

[h=2]The analysis of the server "" returned the following results:[/h][h=2]Port :[/h][COLOR=#225B86][FONT=Ubuntu]Could not ping port. is it forwarded correctly, is it being used at all by SpaceBukkit?[/FONT][/COLOR][h=2]Port :[/h][COLOR=#225B86][FONT=Ubuntu]Could not ping port. is it forwarded correctly, is it being used at all by SpaceBukkit?[/FONT][/COLOR][h=2]Salt:[/h][COLOR=#225B86][FONT=Ubuntu]Server was not reached. Could not [/FONT][/COLOR][check]("http://71.191.206.154/SpaceBukkitPanel/dash#")[COLOR=#225B86][FONT=Ubuntu] Salt.[/FONT][/COLOR]

---

### Post by prodigy_ on 2013-03-28
[http://serverfault.com/questions/140622/how-can-i-port-forward-with-iptables](http://serverfault.com/questions/140622/how-can-i-port-forward-with-iptables)
[http://www.fclose.com/b/linux/816/port-forwarding-using-iptables/](http://www.fclose.com/b/linux/816/port-forwarding-using-iptables/)

---

### Post by 3rdalbum on 2013-03-28
By default, Ubuntu will not block any ports. If you've got a program listening for an incoming connection, it will receive any incoming connection and be able to respond unhindered. No "port forwarding" required.

If you've installed gUFW or some other kind of firewall configuration utility, and you've got it set to block all ports, then just add a new rule to allow ports 2011 and 2012 TCP.

The other thing that might be stopping your connection, if you're attempting to connect to the Ubuntu machine from somewhere outside your network, is your modem/router. Most broadband modems (excluding "dongles") contain some sort of firewall already. You'll need to log into the modem's web-based configuration utility and forward the ports to your Ubuntu machine. The procedure is different for every modem; check your modem's manual.

---

### Post by caleb12134 on 2013-03-28
its not a firewall. it was working like five hours earlier?? Now it cant bind to those ports.????

---

### Post by caleb12134 on 2013-03-28
It didnt work. Any other  suggestions. it says this?? Please can anyone help?? 
[h=2]Port :[/h] Could not ping port. is it forwarded correctly, is it being used at all by SpaceBukkit?[h=2]Port :[/h] Could not ping port. is it forwarded correctly, is it being used at all by SpaceBukkit?[h=2]Salt:[/h] Server was not reached. Could not check Salt.

---

