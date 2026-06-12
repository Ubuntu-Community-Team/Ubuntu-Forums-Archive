---
title: "looking for the right How to for VPN on Ubuntu 16.04"
date: 2016-12-19
forum: General Help
---

### Post by jfaberna on 2016-12-19
I see a lot of OpenVPN howto's but they are fairly elaborate and I want to pick the right one based on what I want to achieve. 

I have a ADSL+ connection to the internet and that modem has WiFi, Port forwarding, etc. and all my computers and devices are on the same subnet. 192.168.0.0/24.

I'd like to be able to remotely login to my home network when on the road and use the network just like I was logged in from one of my home PCs.  The computers that I need access to the most are:

Mythbuntu 16.04 (mythweb on port 80) on a fixed IP within my subnet.
NAS4Free (FreeBSD 11) (WebGUI on port 80) on a fixed IP within my subnet.
File download from any of the PCs.

I'd be doing the remote access from a Macbook Pro.

Any recommendations?

Jim A

---

### Post by btindie on 2016-12-20
The easiest option would be to simply use SSH port forwarding.
You can configure your ADSL router to forward port 2022 from your public IP address to one your your internal hosts on port 22.
Then if you SSH into that host from outside, forward a remote port to a local port, e.g. -L 80:192.168.0.10:80. If you were then to connect to [http://192.168.0.10](http://192.168.0.10) from your mac then connection would actually go to your mythbuntu box.
For this to work with HTTP, you may need to add records to your /etc/hosts file if you're using name based virtual hosts
You could set up external port forwarding for multiple hosts or just use one as a jump box.
Ref: [http://blog.trackets.com/2014/05/17/ssh-tunnel-local-and-remote-port-forwarding-explained-with-examples.html](http://blog.trackets.com/2014/05/17/ssh-tunnel-local-and-remote-port-forwarding-explained-with-examples.html)

---

### Post by jfaberna on 2016-12-20
This sounds like it might work for me. I'll test it and see what happens.

---

