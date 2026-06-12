---
title: "PPTPD and SQL Server"
date: 2013-09-09
forum: General Help
---

### Post by gunksta on 2013-09-09
I have installed PPTPD onto a server that I control. I want to use it as a VPN to a SQL Server database that only allows connections from a white-list of static ip addresses.

I can connect to the VPN and I can ping the SQL Server, but I can not connect to the server (via JDBC) and I don't know why. I can access the web via the VPN without any problem. 

Is there something I have to do to enable forwarding of port 1433? I have disabled ufw (temporarily) so I don't think my firewall is my problem. I used [this guide]("http://silverlinux.blogspot.com/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html") to set up PPTPD.

---

### Post by SeijiSensei on 2013-09-11
By default, MySQL only listens on 127.0.0.1:3306.  If you want it to listen on other IP addresses, you need to [modify my.cnf]("http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html").

You also need to ensure that your users can connect from remote addresses.  They need to named 'user'@'%', or 'user'@'10.10.10.10' if you want to require that specific users connect from pre-designated IPs.

---

### Post by gunksta on 2013-09-12
The database is not the problem. My configuration of PPTPD is the problem. The SQL Server system is a hosted server that is accessible only from a select set of white-listed IP addresses. I have a headless Linux box that is set up on a Static IP xxx.xxx.xxx.126. My work network has an external IP address of xxx.xxx.xxx.125. Both IP addresses are on the white list and should be able to access the SQL Server system. 

From my work network and from the Linux box, I can ping the SQL Server system. Thus proving that the white-list is configured properly. From my house, I can not ping the SQL Server system because my home IP address (dynamic) is not on the list. I have installed PPTPD onto the headless Linux box at 126 so I can VPN and access the SQL Server system. I can connect to the Linux box and I can set up a PPTP VPN. The Internet (port 80) works just fine. Port 22 works as expected too. SQL Server defaults to port 1433 and I can confirm this is how our server is set up.

While sitting in my office at work (xxx.xxx.xxx.125) I can log into the SQL Server system. But, when I connect to the Linux box (xxx.xxx.xxx.126) via PPTPD, I can no longer connect to the SQL Server system. I can however surf the Internet and my IP address is now recognized as xxx.xxx.xxx.126.

In setting up PPTPD, I installed UFW (as per the instructions in the link in the OP) and I followed the directions closely. I also added a command to UFW to allow all SQL Server ports.

Thus. I am stumped.

---

### Post by SeijiSensei on 2013-09-12
Do you have a MySQL login of 'username'@'xxx.xxx.xxx.126'?  Or a login of 'username'@'%'?

What do you see on the server's logs when you are rejected?

---

### Post by gunksta on 2013-09-12
No. I do not have a MySQL login. I'm trying to VPN into a SQL Server database. The SQL Server system is not at .126. The .126 address is just a headless Linux box with PPTPD running on it. 

The SQL Server system is set up correctly. We use it on a half-dozen different projects and I remotely log into it every day. I want to create a VPN system so I can log into when I am on the road and for some reason I'm having port problems with PPTPD or possibly my firewall.

---

### Post by SeijiSensei on 2013-09-12
What addresses are being used for the PPTP connection?  Does the server box have a route to send packets back to you over the VPN?  Can you ping the server box from your end of the PPTP connection?

Suppose your VPN uses 10.1.1.1 and 10.1.1.2 at each end of the tunnel.  Then if you are connecting from 10.1.1.1, the server needs to know how to route packets back to that address.  It would probably need to have a static route added for that purpose.

If you control the PPTPD server, you might try adding a masquerading rule to rewrite the packets' source address with its own.  Something like:

```
/sbin/iptables -t nat -A POSTROUTING -i ppp0 -o eth0 -j SNAT --to-source ip.addr.on.eth0
```

assuming eth0 is connected to the network where the server resides, and your PPTPD connection uses ppp0 for its interface.  This tells the kernel to take traffic designated as going from the PPTP connection to the wired network and replace its source address with the machine's own address on the wired network.  It will then pass the replies it receives back to you.

Edit:  Also what about on your end?  When the PPTP connection is up, is there a route added to your machine that either makes the PPTP connection the system's default route, or adds a specific static route from your machine to the server's network?  If the server resides at, say, 192.168.1.10, you'll need to have a route on your computer that tells it to send traffic for the 192.168.1.0/24 network via the PPTP connection.  Something like

```
/sbin/ip route add 192.168.1.0/24 via 10.1.1.2
```

assuming 10.1.1.2 is the remote end of your PPTP connection.

---

### Post by gunksta on 2013-09-13
Hey, thanks for that. I have been pulling my hair out at work. I'm on vacation next week and I hope to play with your ideas this weekend.

---

