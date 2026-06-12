---
title: "Trouble with Mailserver Config."
date: 2008-03-07
forum: General Help
---

### Post by ShinHadoken on 2008-03-07
Ok, I have my Ubuntu 7.10 Server box all configured as a mailserver (I use Postfix, Dovecot, and OpenWebMail if that means anything to anyone), and I plan to get a domain name. Trouble is, I don't know how to configure it. I have a static IP from my ISP, and on my router I use DHCP, so the server's private IP changes. How do I need to configure this? Do I need to buy an additional IP address for the server? If so, how do I set *that* up? Thanks in advance for the help!

---

### Post by ShinHadoken on 2008-03-07
bump

---

### Post by dcstar on 2008-03-08
> **ShinHadoken said:**
> Ok, I have my Ubuntu 7.10 Server box all configured as a mailserver (I use Postfix, Dovecot, and OpenWebMail if that means anything to anyone), and I plan to get a domain name. Trouble is, I don't know how to configure it. I have a static IP from my ISP, and on my router I use DHCP, so the server's private IP changes. How do I need to configure this? Do I need to buy an additional IP address for the server? If so, how do I set *that* up? Thanks in advance for the help!

Do a search on port forwarding for your router.

---

### Post by ShinHadoken on 2008-03-08
> **dcstar said:**
> Do a search on port forwarding for your router.
Okay (looked it up)....How does this pertain to a web server? I have no idea what to put for application name, or what ports to choose. Now I'm only more confused....

---

### Post by ShinHadoken on 2008-03-08
bump

---

### Post by VorDesigns on 2008-03-11
Hi,
First you need to configure your server with a static IP on the LAN; you will find the settings for this in the interfaces file:
```
/etc/network/interfaces
```
You will need to manually configure:
```
# The primary network interface
auto eth<x>
iface eth<x> inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```
Since I've been busy, I can't remember the if~ restart commands so you could just reboot
```
shutdown -r now
```
Now that you have a staic IP:  You will need to setup your router to pass the necessary ports from your WAN IP Router address to the LAN Server IP address.  The default minimum for a mail transport/POP3 server is TCP port 25 (SMTP) and TCP port 110 (POP3).
Your router should have a guide to do this.
I HIGHLY recommend that you only allow specific port and do not use the Internet server feature that many consumer grade routers have as this will expose your server to potential attack that you don't seem to be prepared for.
If you are going to run a real server; there are few things you should do to make you a good postmaster.
DNS; whatever your domain name you give your server should be properly registered with your DNS hosting provider (ie., kung.foo.net)
rDNS; have your ISP set the rDNS pointer to whatever fully qualified domain name you give your server.  What this does is provide name resolution to your server based on an IP lookup.  Many mail servers are rejecting mail outright from rDNS unqualifiable hosts.
There are many documents here and on the Internet covering the configuration and management of a Postfix server.
Good luck

---

