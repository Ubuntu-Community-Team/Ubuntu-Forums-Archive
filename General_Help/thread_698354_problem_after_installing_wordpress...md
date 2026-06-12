---
title: "problem after installing wordpress.."
date: 2008-02-16
forum: General Help
---

### Post by Mia_tech on 2008-02-16
I installed wordpress to later realize that it installed apache on my kubuntu-box, I didn't want a web server running on my pc so I removed wordpress, but port 80 was still open, then I removed apache2, but after that port 80 is still open...does anybody knwo why?

thanks

---

### Post by shibu on 2008-02-16
hi ... 

Just run the command below to see what's listening on port 80. 

nmap localhost

---

### Post by Mia_tech on 2008-02-16
> **shibu said:**
> hi ... 

Just run the command below to see what's listening on port 80. 

nmap localhost

I've already did.. and apache is running on that port, but here's the output anyway

jorge@kubuntu-box:~$ nmap -sV localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-02-16 09:11 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 1691 closed ports
PORT    STATE SERVICE         VERSION
22/tcp  open  ssh             OpenSSH 4.6p1 Debian 5ubuntu0.1 (protocol 2.0)
80/tcp  open  http            Apache httpd 2.2.4 ((Ubuntu))
139/tcp open  netbios-ssn     Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn     Samba smbd 3.X (workgroup: WORKGROUP)
631/tcp open  ipp             CUPS 1.2
902/tcp open  ssl/vmware-auth VMware GSX Authentication Daemon 1.10
Service Info: OS: Linux

Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap finished: 1 IP address (1 host up) scanned in 11.416 seconds

---

