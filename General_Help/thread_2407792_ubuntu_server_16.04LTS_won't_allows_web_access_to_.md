---
title: "ubuntu server 16.04LTS won't allows web access to various servers..."
date: 2018-12-09
forum: General Help
---

### Post by jdowdster on 2018-12-09
On my local network I had services available only to my local network. The 2 in particular are Plex and Qbittorrent. These are installed and were working just fine for a few years. I then went and tried to install Gitlab on the same server to support my own development. That installation never worked. I got errors when I began to install the "letsencrypt" tool. I gave up on it and left it alone. Later I noticed that now neither of the above mentioned servers (Plex and QBittorrent) are working.

I can see that they are installed and running as services. In fact I even ran on the same server the command:

curl localhost:8080

This should and did access the title page to QBittorrent and the page of HTML code was dumped to my console. So local or same device access works. When I use the URL "http://<my local server IP>:8080/" it never is able to access the page.

I'm looking for advice on where to start checking for problems.

Thanks in advance.

Cheers!!

---

### Post by TheFu on 2018-12-11
Firewall rules?
Perhaps the guide you were following to setup gitlab had rules that block non-gitlab services?

---

