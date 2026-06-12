---
title: "Website Accessible from outside network but not from inside the network."
date: 2014-06-04
forum: General Help
---

### Post by Stephen_Brown on 2014-06-04
I have just upgraded my Ubuntu Desktop system and I have been running websites on it and using dns2go to serve them. I am able to access HTTP, FTP and SSH from outside the local network with no problems but when ever I try to access it on the same network the server can not be found. If I enter the ip address 192.168.2.2 the site comes up but not if I enter the address xxxxxxx.myip.org? Not sure whats going on here.

I do have some errors when the Ubuntu system starts but there dosn't seem to be an explination as to what the problem is.
When I upgraded I did need to change my DocumentRoot from /var/www/html to /var/www to get the site to appear.

- Any ideas or instructions appreciated.
- Stephen Brown

---

### Post by TheFu on 2014-06-04
Welcome to the forums.

I don't know anything about dns2go sorry.

From outside, the name-to-IP gets resolved to your public IP - as it should.
From inside, the  name-to-IP gets resolved to your public IP too and some routers that see this will block it - a security measure.  Which router is being used and have you replaced the firmware with a better firmware like tomato, dd-wrt, openwrt, or something else?

Can you access the HTTP, SSH from inside using the local LAN address or names you've shared across all the internal systems in the /etc/hosts files?

I don't believe the issue is related to any server-side settings.

BTW, [FTP really shouldn't be used by 99.9999% of the world anymore]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") (should have stopped using it 15 yrs ago really).

---

