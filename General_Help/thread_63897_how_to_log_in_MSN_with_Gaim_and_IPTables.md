---
title: "how to log in MSN with Gaim and IPTables?"
date: 2005-09-09
forum: General Help
---

### Post by cristianommxp on 2005-09-09
[SIZE=2]Hi, 

I have a problem. 

I use iptables for my personal firewall.

I cant log in to MSN with Gaim and I cant log in to my Gmail inbox with Evolution.

Actualy, this are my iptables chains:

[FONT=Courier New] 

01 sudo iptables -P INPUT ACCEPT
02 sudo iptables -P FORWARD DROP
03 sudo iptables -P OUTPUT DROP
04
05  sudo iptables -A INPUT -p tcp --syn -s 127.0.0.1/255.0.0.0 -j ACCEPT
06  sudo iptables -A INPUT -p tcp --syn -j DROP
07
08  sudo iptables -A OUTPUT -s 127.0.0.1 -j ACCEPT
09  sudo iptables -A OUTPUT -s 172.16.23.22 -d 172.16.23.21 -j ACCEPT
10  #to accept web services connections
11  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 80 -j ACCEPT
12  #to accept e-mail connections
13  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 25 -j ACCEPT
14  #to accept Jabber connections
15  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 5222 -j ACCEPT
16  #to accept MSN connections
17  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 1863 -j ACCEPT
[/FONT]

Where 172.16.23.22 is my IP and 172.16.23.21 is my DNS server.

Well, the line number 15 (Jabber) and 11 (Firefox browser) it's work all fine.

But I think there's something wrong to line 13(email) and 17 (MSN).

So, what's wrong with my chains?

[/SIZE]

---

### Post by goedson on 2005-09-09
[QUOTE=cristianommxp][SIZE=2]Hi, 

I have a problem. 

I use iptables for my personal firewall.

I cant log in to MSN with Gaim and I cant log in to my Gmail inbox with Evolution.

Actualy, this are my iptables chains:

[FONT=Courier New] 

01 sudo iptables -P INPUT ACCEPT
02 sudo iptables -P FORWARD DROP
03 sudo iptables -P OUTPUT DROP
04
05  sudo iptables -A INPUT -p tcp --syn -s 127.0.0.1/255.0.0.0 -j ACCEPT
06  sudo iptables -A INPUT -p tcp --syn -j DROP
07
08  sudo iptables -A OUTPUT -s 127.0.0.1 -j ACCEPT
09  sudo iptables -A OUTPUT -s 172.16.23.22 -d 172.16.23.21 -j ACCEPT
10  #to accept web services connections
11  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 80 -j ACCEPT
12  #to accept e-mail connections
13  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 25 -j ACCEPT
14  #to accept Jabber connections
15  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 5222 -j ACCEPT
16  #to accept MSN connections
17  sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 1863 -j ACCEPT
[/FONT]

Where 172.16.23.22 is my IP and 172.16.23.21 is my DNS server.

Well, the line number 15 (Jabber) and 11 (Firefox browser) it's work all fine.

But I think there's something wrong to line 13(email) and 17 (MSN).

So, what's wrong with my chains?

[/SIZE][/QUOTE]


You're using the wrong port for Gmail access. 25 is the SMTP port. You should open the secure POP3 (995) port.

I don't know about MSN, but it may be the same problem.

---

### Post by cristianommxp on 2005-09-09
ok, 

10ks Goedson. Now I can access my GMail inbox.

But, I need too access MSN. 

What to do now?

---

### Post by goedson on 2005-09-13
[QUOTE=cristianommxp]ok, 

10ks Goedson. Now I can access my GMail inbox.

But, I need too access MSN. 

What to do now?[/QUOTE]

The MSN authentication is  done through HTTPS, so you should open the port number 443. A line like:

```
sudo iptables -A OUTPUT -s 172.16.23.22 -p tcp --dport 443 -j ACCEPT
```

in your script should do the trick.

---

