---
title: "everything stop working after 2 commands?"
date: 2013-04-25
forum: General Help
---

### Post by albin2009 on 2013-04-25
Hey you all, im reaching out here!

So i got my mysql server and apache server working perfect and also all my servers(Counter-Strike, SA:MP Minecraft) working perfectly.
My websites are running to a 100% and there is no problem.
So i tried connect my server to a site called [www.gametracker.com](www.gametracker.com) wich is a server tracker website with live server banners, but i didn't work so i though maby i need to open the ports in ubuntu or maby i need to shut off the firewall.

So i went to google and search for: How to open game query port in ubuntu and came up with this command:
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 9987 -j ACCEPT (9987 is the port for my teamspeak 3 chanel, its a voice server)

It didn't work so i went to google and search for: Ubuntu turn off firewall and found tihs command:
$ sudo ufw disable

After these two commands, i cant acces to my websites, my servers only works on local network, noone els can connect to the server...

I cant quite understand why these two commands f*** up my whole system?

Please help you guys, im desperate.

---

