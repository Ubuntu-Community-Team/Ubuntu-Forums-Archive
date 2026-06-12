---
title: "Samba client"
date: 2013-06-13
forum: General Help
---

### Post by JanezMurn1988 on 2013-06-13
Hello folks,

I have joined my system into the windows domain with the likewise-open program successfully. Now I have a probmem. I can't access to the data as a domain user with the limit access to the folders.
If I try with the Dolphin (smb://server_name) it connects as "Everyone" user. Changes in the smb.conf file have no effect. I don't know what else to do. I've noticed somewhere that it is possible to login
into the system as a domain user, but on the login screen the name is fixed. You can't change it into like domain/user... If anyone can help me with this I will really appriciate it.

Best regards,

Janez

---

### Post by HermanAB on 2013-06-13
Something like this:
smb://user:domain@server

---

### Post by JanezMurn1988 on 2013-06-17
It doesn't work... It connects as Everyone with limited access.

---

### Post by JanezMurn1988 on 2013-06-17
Example "smb://master@10.13.10.7/27 Tehni&#269;na dokumentacija/" or "smb://10.13.10.7/27 Tehni&#269;na dokumentacija/" there is no difference... Any other idea??

---

### Post by JanezMurn1988 on 2013-06-17
I have found a solution. I've tried to connect with Dolphin, Nautilus, ... unsuccessfully... PCManFM did the magic (smb://user@host). 
SOLVED

---

