---
title: "After upgrading to 7.04, I cannot connect many website. help plz"
date: 2007-05-24
forum: General Help
---

### Post by grabbit on 2007-05-24
Dear all,

I upgrade my desktop in my university from Edgy to 7.04 using update manager. Then I find I cannot connect most website except [www.google.co.uk](www.google.co.uk) and [www.mozilla.org](www.mozilla.org). however, i can ping all website at the same time. My desktop using a static IP address.

Due to the same reason, I cannot run "apt-get update " any more. Because I can only ping those repository server, but cannot log in.

I have a Acer laptop with the same problem, but it can connect smoothly with Dynamic IP address and broadband at home. So why?

As for firewall, there is only iptables installed by default in Ubuntu.

Please give me any hints, thanks a lot.

---

### Post by disposable on 2007-05-24
Has the university started to filter web sites or is your connection sporadic? Have you double-checked DNS? I would methodically test your connection from your NIC out -- is the NIC configured correctly and do the lights blink when you ping, can you reach your local gateway, can you reach a university DNS or web server, finally, can you reach the web?

Eliminate as you go and good luck!

---

### Post by pragmatine on 2007-05-24
Does your university require you to use (and authenticate with) a proxy server to access web content?

---

### Post by grabbit on 2007-05-25
There is a firewall in our department, but it is open for static IP address which is assigned by computer support team. 

I have both windows XP and ubuntu 7.04 in the same desktop
i still have no idea why I can use internet smoothly in XP , but the same time I can only access very limited website in Ubuntu 7.04. Although there is a firewall, but in ubuntu I can ping every website, but unable to access  
most of them through firefox or opera in linux. 

So is what happened to my laptop (dynamic IP) when I use it in department. When I use it at home (still dynamic IP), no problem at all. So what's the difference?:(:(

---

### Post by grabbit on 2007-05-25
BTW, in Ubuntu 7.04 I even can use google to do a search, but once i click the link of the results, no website can be connected. The exception is [www.mozilla.org](www.mozilla.org). I can connect that. But I cannot connect sun's firefox java plugin from mozilla due to same unknown reason

---

