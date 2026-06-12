---
title: "Cannot connect to nodejs app on port 3001"
date: 2021-06-08
forum: General Help
---

### Post by alouqua on 2021-06-08
I have two nodejs applications (server A and server B) running on Ubuntu Server 16.04, and two clients (client A and client B) that make requests to that servers.

Server A listens for requests from client A on TCP port 3000 and everything works fine.
Server B listens for requests from client B on port 3001. In this case, client B never manages to connect (Error: timeout).
If server B listens on port 3000, client B also works fine. But client A fails to connect to server A on port 3001.

Test from localhost:
```
lsof -i -P -n | grep LISTEN
node\x20/ 1409     root   23u  IPv6  18686      0t0  TCP *:3001 (LISTEN)
node\x20/ 1764     root   23u  IPv6  24445      0t0  TCP *:3000 (LISTEN)

```

```
root@localhost:~# nmap localhost
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
143/tcp  open  imap
443/tcp  open  https
3000/tcp open  ppp
3001/tcp open  nessus
3306/tcp open  mysql
8080/tcp open  http-proxy

```

Test from remote machine:
```
nmap -P0 82.223.25.XXX
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
3000/tcp open  ppp
8080/tcp open  http-proxy

nmap -p 3001 82.223.25.XXX
PORT     STATE    SERVICE
3001/tcp filtered nessus

```

Firewall:
```
root@localhost:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3001

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
       
root@localhost:~# ufw status
Status: inactive

```

I have tried to open ports with ufw without success.

---

