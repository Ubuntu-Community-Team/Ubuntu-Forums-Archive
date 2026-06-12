---
title: "Networking problem after upgrade to 12.04 LTS"
date: 2013-06-05
forum: General Help
---

### Post by DoverHarpist on 2013-06-05
I recently updated the Ubuntu Linux OS on a computer I use as a web server. (target OS was  Ubuntu 12.04 LTS. I am uncertain what I started with, but the OS was installed about 6 months ago). The upgrade seemed to have gone well, and the web page came up with no problem on that computer (using localhost or the IP address). But none of the services (web, FTP, etc…) are accessible from other computers in my home network or from computers outside the network.

The computer is accessible on the network and I can ping it, but if I try FTP or HTTP from any other computer, I get no contact. Any suggestions. Any and all assistance would be welcome.

Thanks

Harpist

---

### Post by newbie-user on 2013-06-05
Check any firewalls you might have set up. Also, check that your FTP and web services are running.

---

### Post by DoverHarpist on 2013-06-05
> **newbie-user said:**
> Check any firewalls you might have set up. Also, check that your FTP and web services are running.


FTP and HTTP services are running (if I try starting them again, it tells me that they are already running) and the only "firewalling" I am doing is denying some IPs using the "deny" section in the Apache HTTP server configuration file - httpd.conf.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by DoverHarpist on 2013-06-05
> **ahallubuntu said:**
> When you install Apache2 on a clean installation, it should automatically open port 80.  But because you upgraded - ?  Same with FTP.

See if the ports for Apache2 and FTP are open by installing nmap, then run a scan (from the command line of the Ubuntu machine):

```
nmap localhost
```

If the ports are closed...you could try removing Apache2 and re-installing (your config files probably won't be erased, but it's easy to back them up before you remove Apache2).  See if doing this opens the Apache ports.  If so, do the same with whichever FTP server you are using.

nmap shows the following ports open

21
80
139
443
445
3306
5800
5900

---

### Post by DoverHarpist on 2013-06-05
I need to modify the answer on the nmap scan. When I run the nmap scan on the computer with the web server, it tells me that all the required ports are open. But when I run an nmap scan on another computer (but targeting the computer with the web server), it gives me zero open ports (and zero closed with 1000 filtered ports). 

Is there a firewall I have missed because suddenly, i'm uncertain that the answer I gave the first responder is correct. The Firewall configuration program I use for configuring the ufw firewall shows  IP addresses that ate denied (and these do not included any that I am using for this test), but no other firewall rules.

DoverHarpist

---

### Post by DoverHarpist on 2013-06-05
Hi folks,

It was indeed a ufw firewall issue. Some type of "default" firewall got loaded and enabled. Once I disabled this, everything was fine.

Thanks for all the help

DoverHarpist

---

