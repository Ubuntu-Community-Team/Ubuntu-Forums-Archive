---
title: "Synaptic Package Manager - Repository Error - connect (111 Connection refused)"
date: 2006-07-11
forum: General Help
---

### Post by flub on 2006-07-11
I've tried to run the Sysnaptic Package manager and when I hit "reload" it pulled up the "download 1 or 5" box but then when straight to this screen of errors.

Any ideas why it is trying to connect to 192.168.1.101???

Note: PC is a laptop which connects wirelessly to a a LinkSys router connect to cable modem.I can browse and email etc with no problems.



[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to 192.168.1.101:8080 (192.168.1.101). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to 192.168.1.101:8080 (192.168.1.101). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to 192.168.1.101:8080 (192.168.1.101). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to 192.168.1.101:8080 (192.168.1.101). - connect (111 Connection refused)
[http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg:](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg:) Could not connect to 192.168.1.101:8080 (192.168.1.101). - connect (111 Connection refused)

---

### Post by flub on 2006-07-11
Just thought I'd add that the router is also link to a Desktop pc running XP Sp2

---

### Post by flub on 2006-07-11
FIXED - Under my System/Prefrences/Network Proxy I had some old proxy setup. Cleared it and now all ok.

---

