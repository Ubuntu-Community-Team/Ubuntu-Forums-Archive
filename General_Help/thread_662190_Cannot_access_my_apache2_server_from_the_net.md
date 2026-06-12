---
title: "Cannot access my apache2 server from the net"
date: 2008-01-08
forum: General Help
---

### Post by sandydesu on 2008-01-08
As the title suggests, I cant access my apache2 server from the net. Pertinent facts are:

1) localhost access is fine.

2) My server is listening on 91.84.110.99:50000. Its a static IP and the reason for the unusual port number was in case my ISP was blocking certain ports.

3) I have removed my firewall, flushed my iptables and set all policies to accept. By usinf iptables -L i now get this:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain f0to1 (0 references)
target     prot opt source               destination         

Chain f1to0 (0 references)
target     prot opt source               destination         

Chain logaborted (0 references)
target     prot opt source               destination         

Chain logaborted2 (0 references)
target     prot opt source               destination         

Chain logdrop (0 references)
target     prot opt source               destination         

Chain logdrop2 (0 references)
target     prot opt source               destination         

Chain logreject (0 references)
target     prot opt source               destination         

Chain logreject2 (0 references)
target     prot opt source               destination         

Chain nicfilt (0 references)
target     prot opt source               destination         

Chain s0 (0 references)
target     prot opt source               destination         

Chain s1 (0 references)
target     prot opt source               destination         

Chain srcfilt (0 references)
target     prot opt source               destination         

Im at a loss and mildly annoyed. If anyone could help me and also teach me somthing useful in the process I would be grateful.

---

### Post by yaztromo on 2008-01-08
Well here's nmap's output for your server

```

nmap 91.84.110.99 -P0 -p 50000

Starting Nmap 4.20 ( http://insecure.org ) at 2008-01-09 00:00 GMT
Interesting ports on 91.84.110.99:
PORT      STATE  SERVICE
50000/tcp closed iiimsf

Nmap finished: 1 IP address (1 host up) scanned in 0.088 seconds

```

So for me the port isn't blocked (iptables dropping all packets) but is closed. 

In /etc/apache2/ports.conf you should have "Listen 50000" in there and in /etc/apache2/sites-available/default you should have "allow from all" in the /var/www/ section.

If you type netstat -l in a terminal you should see something like
tcp6       0      0 *:50000                  *:*                     LISTEN

---

### Post by PinkFloyd102489 on 2008-01-08
Sure apache is running?


If you're behind a router, you need to forward 50000 also.

---

