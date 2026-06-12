---
title: "Routing IPs is it possible?"
date: 2006-11-14
forum: General Help
---

### Post by FeraTech on 2006-11-14
Hi, I was just wondering. Over the summer I realized my server was hacked by spammers. Seems as though my dynamic IP was block and I can't send e-mails out from my server anymore on port 25.

I have actually gotten around this problem temporarily by using PHP script to remotely connect to an SMTP server and then send out the e-mail.

Is it in any possible to route my Dynamic IP address through another one? 

I'm simply looking for a way to make it seem as though the IP I am at is a different one.

---

### Post by adwait on 2006-11-14
It doesn't matter what routes you add to a router, the packets sent by your machine will always contain your IP address in the source field of the IP packet. If you want it to appear like you are on a different IP, you need a proxy. A proxy will take your packets, replace the source field with there own IP so it will seem like the packets came from there. The replied will then be forwarded to you..thus effectively hiding your actual IP address. But for that, you first need to find a proxy server allowing  unrestricted access.

---

### Post by FeraTech on 2006-11-14
Now if I had a proxy server people would be able to type the IP of that proxy server and it would be routed to mine, correct? Now, would that work in reverse too? If I'm browsing a site would it show the IP of the proxy server or my server?

---

### Post by adwait on 2006-11-15
If you are browsing a site, the site will see the requests comaing from the server, ie: it will see only the proxy server IP, not yours. 

If people type in the IP of the proxy, it could be redirected to you if you actually own the proxy. If you just use one of the proxies available on the net, it might not be redirected to you because that proxy server is shared by many.

---

