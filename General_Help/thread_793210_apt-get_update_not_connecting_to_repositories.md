---
title: "apt-get update not connecting to repositories"
date: 2008-05-13
forum: General Help
---

### Post by cbope on 2008-05-13
6.06 LTS / AMD64 server version

This is my web/ftp server and has been running 6.06 LTS ever since it came out. Everything has been ok until recently. I had to shut down the server for about 2 months while I moved and did some renovation on our new old house. I just recently put the server back online, but apt is not able to establish connections to the update repos. I get connection timed out errors. I have been using fi.archive.ubuntu.com mirrors (I'm in Finland). I edited my sources.list and tried the Swedish mirrors (se.archive.ubuntu.com) and finally the main servers, but all I get are time outs. Everything was fine before the move, I ran an apt-get update just before shutting the server down for the move. I'm still with the same ISP, and internet services seem to be fine.

Why is apt not able to establish connections with the repos?

---

### Post by pointone on 2008-05-14
Could you post your sources.list file and the output of running "apt-get update"?

Are you able to ping the repositories?

---

### Post by cbope on 2008-05-14
> **pointone said:**
> Could you post your sources.list file and the output of running "apt-get update"?

Are you able to ping the repositories?

I'll post the info when I get home. One thing sticks in my mind now, maybe I have a DNS problem. I believe that apt shows the IP address for each repo as it connects, and for some reason it shows something like 1.0.0.0. Maybe ubuntu is not resolving DNS names to IP's properly anymore, after I moved. I didn't test it with a web browser because this server is headless and runs without X, I SSH into it from my Windoze workstation to update and perform maintenance.

---

### Post by cbope on 2008-05-14
Nevermind, it was a DNS problem as I suspected. I was troubleshooting a wireless connection issue with my router/gateway last week and I performed a full router reset. DNS relay was enabled after the reset and for some reason this doesn't work well with linux and this particular router. After turning DNS relay off and setting the correct DNS server, it's able to get updates again. Really strange, because the DNS relay when enabled, works fine with my Windoze boxen.

---

