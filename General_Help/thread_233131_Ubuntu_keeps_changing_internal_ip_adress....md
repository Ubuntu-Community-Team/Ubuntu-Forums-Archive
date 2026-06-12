---
title: "Ubuntu keeps changing internal ip adress..."
date: 2006-08-09
forum: General Help
---

### Post by Kodai on 2006-08-09
Hey all, i've got Ubuntu to work perfectly. Everything I want of it is great, except one thing. it constantly switches between 192.168.0.6 and 192.168.0.4 everytime it restarts. I don't like this because it messes with my port forwarding. :( Any assitance?

---

### Post by kerry_s on 2006-08-09
Do you have it set to static? If it's on dhcp it will use what ever address it is given.

---

### Post by Kodai on 2006-08-09
no. i'll give that a shot. and for the ip just put 192.168.0.6?

---

### Post by Kodai on 2006-08-09
ok, so i turned it to a static IP, w/ my ip adress 196.168.0.6, and subnet 255.255.255.0, and gateway blank because i don't know what to do with that. Good news: router says it's on x.x.x.6 now, bad news, it can't connect to the internet :( . Any help!!! thanks

---

### Post by Bumblescrump on 2006-08-09
try restarting.

---

### Post by DoktorSeven on 2006-08-09
Gateway has to be the (local) IP address of your router (probably 192.168.0.1).  

You also have to be sure that /etc/resolv.conf contains your ISP's DNS servers, or your router IP if it acts as a DNS.  Check your router information for DNS addresses.  Each DNS IP goes on a separate line, with the word **nameserver** in front of it.

---

