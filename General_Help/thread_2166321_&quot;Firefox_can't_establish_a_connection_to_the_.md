---
title: "&quot;Firefox can't establish a connection to the server at&quot; with Apache2"
date: 2013-08-08
forum: General Help
---

### Post by Peptid on 2013-08-08
Hello All,

I recently installed Apache2 server on my laptop along with mysql and php5. Then, I installed Wordpress.

I can access the content of the website in the server from my laptop, which contains Apache2 server; however, from other computers which are not in my network I cannot access the content and constantly receive "Firefox can't establish a connection to the server at" error. From Safari at my iphone I get "server stopped responding" error. 

There are no other IP addresses than mine at 'access.log' file of Apache.

I believe I am missing a point but cannot identify. I am using Kubuntu 12.04, by the way.

---

### Post by Peptid on 2013-08-09
OK, since no one has replied yet, I think I figured out the problem; yet I still do not know how to solve it.

The problem was I tried to access my local server 192.168.2.2 outside the network, which cannot find my server. Now, I know that I need to forward every incoming requests to my WAN IP to local IP (192.168.2.2) but I do not know how to do this.

Anyone can help me to configure httpd.conf (or similar files) in Apache2 to solve the problem?

---

