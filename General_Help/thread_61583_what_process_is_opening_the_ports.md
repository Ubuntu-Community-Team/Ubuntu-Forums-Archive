---
title: "what process is opening the ports?"
date: 2005-09-01
forum: General Help
---

### Post by cristianommxp on 2005-09-01
Hi,

I executed nmap to discovery what ports my PC keep opened.

The result is bellow:

===================================================
$ nmap localhost

Starting nmap 3.50 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-01 10:54 BRT
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1653 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
25/tcp  open  smtp
80/tcp  open  http
111/tcp open  rpcbind
631/tcp open  ipp
640/tcp open  unknown
841/tcp open  unknown
===================================================

I have some questions:

1) What do I have to do to know what process is opening the ports?

2) How to close them?

3) Why is there a smtp port open if I haven't a e-mail server?

4) How to discovery what means "unknown" process?


10ks.


Cristiano

---

### Post by nemin on 2005-09-01
[QUOTE=cristianommxp]
[nmap scan]
1) What do I have to do to know what process is opening the ports?[/QUOTE]I think you'll find this command very usefull:
```
sudo netstat -lntp
```
[QUOTE=cristianommxp]2) How to close them?[/QUOTE]Use a firewall or close the program that opens the port. I'd advise you to have a look at "iptables".
[QUOTE=cristianommxp]
4) How to discovery what means "unknown" process?[/QUOTE]You can google which program/service/protocol usually uses this port.

---

### Post by KingBahamut on 2005-09-01
apt-get install firestarter 

Run firestarter and setup. 

Filter and or Remove the ports you wish.

---

### Post by rmjokers on 2005-09-01
Another thing to note is that some of the ports you have listed may only be open to the local machine.  For example, the SMTP port is, by default, open to traffic from the local machine to itself so that the root user can get emails about system information.  However, this port is NOT open to the outside.  In order to get an idea of what ports are open to remote users, you could nmap your IP address rather than your localhost address.  You should no longer see the SMTP port in this case unless you have configured the mail server to accept remote connections.

---

