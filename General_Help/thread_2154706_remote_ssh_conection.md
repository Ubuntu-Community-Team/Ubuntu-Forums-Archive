---
title: "remote ssh conection"
date: 2013-06-15
forum: General Help
---

### Post by steve701 on 2013-06-15
Hi all: my ssh daemon is running fine and internally I can ssh into my ubuntu from my other PC's from my home Network.
The daemon starts in /etc/init.d/ssh

The problem is when I try to ssh from remote (my work location), it does not make a connection. The port open is 22. Why can I not connect from outside?
The config file is located at:  /etc/ssh/sshd_config    Is there a setting in here that controls remote connection to my ssh server?

Thanks,
Steve

---

### Post by Doug S on 2013-06-15
Very often work networks will not allow ssh traffic outgoing.
If that is not the problem, then you might need port forwarding for port 22 from your router to your ubuntu box on your lan.

---

### Post by steve701 on 2013-06-15
I just checked my router, both 21 (ftp) and 22 (ssh) are listed as enabled for forwarding.

And FTP(21) works perfectly fine from my work-->home, so I would have thought that ssh would work also.

---

### Post by Lars Noodén on 2013-06-15
You might check to see if you can get through to port 22 from the outside.  Canyouseeme is one service that can test that:
[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by HiImTye on 2013-06-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I like GRC's because you can specify a range of ports, or common service ports, etc
[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)
your ISP could be blocking it, if your firewall is set default deny, you could be blocking it, or your work network (more likely) or ISP (less likely, but possible) could be blocking it. check if your ISP blocks port 80 or 443 by setting ssh to that port. those are the ports most likely to bypass your work's firewall

---

### Post by steve701 on 2013-06-15
Hey thanks, tried that, 22 is wide open...hence it is likely my work who is blocking it....but is there a technical way to verify that when I am at work (without asking them)?

---

### Post by markbl on 2013-06-16
> **steve701 said:**
> Hey thanks, tried that, 22 is wide open...hence it is likely my work who is blocking it....but is there a technical way to verify that when I am at work (without asking them)?
Corporate firewalls usually block port 22 (ssh) outbound because users can set up reverse tunnels, dynamic proxies, etc via the ssh connection and that make the corporate administrators shudder. For this reason I forward port 443 (normally https) from my home router to port 22 on my linux server. It is much harder for the corporate firewall to selectively block port 443 out and I have never seen one that does. This assumes of course that you are not running a https server at home which is usually the case. So then just connect to your home box from within the corporate lan via port 443, i.e. "ssh -p443 [email]me@myhome.no-ip.biz[/email]".

---

### Post by Lars Noodén on 2013-06-16
> **markbl said:**
> ...This assumes of course that you are not running a https server at home which is usually the case. So then just connect to your home box from within the corporate lan via port 443, i.e. "ssh -p443 [email]me@myhome.no-ip.biz[/email]".

Actually you can [multiplex using sslh](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Multiplexing#Multiplexing_HTTPS_and_SSH_Using_sslh) and have both HTTPS and SSH over the same port.  I can't speak to how efficient it is but it is easy enough to install.  If it is not a high-traffic web site, [sslh](http://www.rutschle.net/tech/sslh.shtml) probably does not affect performance much.

---

