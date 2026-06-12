---
title: "Port checking software?"
date: 2020-03-01
forum: General Help
---

### Post by zefk on 2020-03-01
I wanna check if my port is open or closed at all times (Kinda like a display) and an alarm to sound off or some push notification that will let me know if it is closed.

For instance, I can check if my port is open with: [https://canyouseeme.org/](https://canyouseeme.org/)

---

### Post by TheFu on 2020-03-01
netstat
lsof

Write a little script for the notification you want.

---

### Post by HermanAB on 2020-03-02
Bear in mind that a port is just a number in the IP header.

For a connection to be established, you need to have a listener on the port.  So if your machine isn't running any servers then there are no open ports.


If you want to know what is going on with your ethernet interfaces, learn how to use tcpdump.

---

### Post by The Cog on 2020-03-02
Be clear what you mean here. 
As far as the OS is concerned, there are two possible port states:
* Open : There is an application listening on that port for incoming connections
* Closed : No application is listening. It will respond t any connection request with connection refused.

Firewalls along the way can interfere with connection attempts though. In general they will do one of three things:
ACCEPT : Allow the connection to pass unhindered
DROP : Drop the connection request (or the returning response) - this causes "No reponse" or "Timeout" errors.
REJECT : Send a connection refused instead of letting a connection request pass through.

So as for Open or Closed, you can see this by locally running the command (e.g. looking for state of port 22):
```
ss -lnt
```
and see if it lists 22 as listening. 
Of course, this says nothing about the behaviour of any firewalls along the path between two machines which could be dropping or rejecting connection attempts.

A favourite of mine for testing reachability is to use nc (netcat) e.g.
```
nc -vz 1.1.1.1 22
```
which will tell you Success (port is open), Refused (port is closed or a firewall rejected), or Timeout (network problem or firewall drop).

---

### Post by HermanAB on 2020-03-02
Well, there are billions of ports.  Watching them is kinda pointless.

---

### Post by SeijiSensei on 2020-03-03
I'd use [nmap]("https://insecure.org/").  If you don't have access to a machine outside your network from which you can run nmap, there are online services that will run a scan for you like [http://nmap.online-domain-tools.com/](http://nmap.online-domain-tools.com/).

You can't really expect to keep testing ports repeatedly in real-time. Construct a set of firewall rules that meet your needs and be done with it.

---

### Post by HermanAB on 2020-03-03
+1 for nmap.

Trying to watch ports is like trying to brute force your own name by testing a complete permutation of the alphabet.  Since you already know your own name, you don't need to do that.

So, watch the servers that you are running, don't watch whatever ports they may be using.

---

