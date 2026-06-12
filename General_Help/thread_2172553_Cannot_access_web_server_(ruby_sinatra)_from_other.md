---
title: "Cannot access web server (ruby sinatra) from other computers"
date: 2013-09-05
forum: General Help
---

### Post by AvitarX on 2013-09-05
I have setup a simple file search using Ruby and Sinatra.  It worked on my old computer, but not on my new install.

I don't remember the version of the old computer when it died, but I copied the small application from the backup. It works perfectly from my local computer, but not over the network.

Any help would be useful, I looked about the internet, and had no results, not knowing what to search, the obvious answer to me (a firewall) does not appear to be the case.

Output below.

from said computer:

```
$ uname -a
Linux Design-Studio-Server 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```


```
$ sudo ufw status
Status: inactive

```

```
$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:4567          *:*                     LISTEN     

```


```
$ sudo iptables -L
[sudo] password for drake: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        
```


```
$ nmap -p 4567 127.0.0.1

Starting Nmap 5.21 ( http://nmap.org ) at 2013-09-05 11:44 EDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000037s latency).
PORT     STATE SERVICE
4567/tcp open  unknown

```




```
$ nmap -p 4567 127.0.1.1

Starting Nmap 5.21 ( http://nmap.org ) at 2013-09-05 11:44 EDT
Nmap scan report for Design-Studio-Server (127.0.1.1)
Host is up (0.000034s latency).
PORT     STATE  SERVICE
4567/tcp closed unknown

```


From a different computer:

```
$ nmap design-studio-server -p 4567

Starting Nmap 5.21 ( http://nmap.org ) at 2013-09-05 11:46 EDT
Nmap scan report for design-studio-server (10.170.2.1)
Host is up (0.00029s latency).
PORT     STATE  SERVICE
4567/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.14 seconds
```

---

