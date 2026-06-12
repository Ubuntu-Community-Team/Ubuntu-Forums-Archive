---
title: "Remote access to computer behind router"
date: 2007-01-14
forum: General Help
---

### Post by vigleik on 2007-01-14
The following question probably either has a very simple or a very complicated answer. The information is probably "out there", but I haven't figured out the right way to google for it. If I want remote access to another computer (running whatever version of linux, in this case ubuntu edgy eft) and it has its own IP address, I know many ways to do it. For example, ssh or sftp. My question is this: Can I do something similar if the computer I want to access sits behind a router, without its own IP address? Do I need to do something weird to the router first? I have a regular linksys router, and I think it usually gives me an address like 192.168.0.10, though I can't figure out how to find that out right now. A solution that doesn't require changing the setup for the router would be best.

---

### Post by rabid9797 on 2007-01-14
well if your trying to do a remote access such as vnc or the like, all you need to do is forward the right ports to that computer from your router.

are you trying to setup your computer for remote access or another computer on a different router(e.x. your friend's computer at their house) for remote access?

---

### Post by vigleik on 2007-01-14
I don't know what vnc is, and I don't know how to set up port forwarding from the router, so detailed instructions would be very helpful. Barring that, a hint about which program to use/which config file to edit would be good too. I don't usually feel like this much of a newbie, but I guess in this case I am.  If they could only get on with IPv6 every computer could have its own IP address, and I wouldn't have this problem.

Anyway, I am trying to set up my own computer for remote access. Both my desktop, so I can download the occational file from elsewhere, and my mythtv box, so I can administer it remotely.

---

### Post by jflash on 2007-01-14
What kind of router do you have? We can't give detailed directions without knowing what router you have.

---

### Post by vigleik on 2007-01-14
The router is a regular Linksys router, it claims to be a Wireless-G Broadband Router WRT54G. Under the setup -> Applications & Gaming, it looks like I can set up port forwarding. And now I'm making progress :D. Doing the following made ssh work:

Application: ssh
Start: 22
End: 22
Protocol: both (choices are both, tcp and udp)
IP Address: 192.168.1.107
Enable: yes

I guess I can even make this work for more than one computer by using (for example) port 22 for one and port 23 for the other.

In principle this is very good. In practice, there are a couple of problems still. One, the IP address for the router changes from time to time, though probably not very often. And two, the "local" IP address for each of my computers change (I think) every time I reboot. If there are no easy solutions to these problems I understand, but I'll ask anyway. Does anyone know how to deal with that?

---

### Post by rabid9797 on 2007-01-14
the solution in this case is setting up a static IP for the computers you want to access.

this article might be too technical but i think this is exactly what your looking for:
[http://www.securityfocus.com/infocus/1816](http://www.securityfocus.com/infocus/1816)

EDIT:

try this:
[http://ubuntuforums.org/showthread.php?t=247563&highlight=static+IP](http://ubuntuforums.org/showthread.php?t=247563&highlight=static+IP)

---

### Post by vigleik on 2007-01-14
This is great stuff, thanks a lot. Getting a static IP address from my ISP is not going to happen, I think they charge....maybe 100$ extra per month for that. Which is just crazy. But using [http://www.dyndns.com/](http://www.dyndns.com/) to get a domain name and using the script found in [http://ubuntuforums.org/showthread.php?t=247563&highlight=static+IP](http://ubuntuforums.org/showthread.php?t=247563&highlight=static+IP) seems to be exactly right for me. Thanks again.

---

### Post by jflash on 2007-01-14
Not sure if this issue has been addressed, but to use static IPs on your computers, disable DHCP on the router under General Settings (I think), and then assign IP addresses manually to each machine (this is done on the individual machine).

---

### Post by celticmonkey on 2007-02-10
About static IPs, you generally don't need to disable the DHCP on your router. You just need to know what range of IPs the router assigns using DHCP. 

For instance, many routers are setup to automatically assign up to 50 address in the range 192.168.1.100 - 192.168.1.150. All you need to do is change the network settings on your local machine (via System -> Networking) to use an IP outside that range (ie. 192.168.1.151) that no other computer on the LAN is using.  No need to change any router settings.

However, you may need to make a note of what DNS your ISP is using first because you won't get it from the router automatically anymore. (Or use a DNS service like opendns.com). 

The IP ranges I used as examples may be different for your router. Login to your router to find the ranges set for your model.

---

