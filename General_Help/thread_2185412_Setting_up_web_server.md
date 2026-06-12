---
title: "Setting up web server"
date: 2013-11-02
forum: General Help
---

### Post by vangend.robert on 2013-11-02
Hello All,


Before I begin, I want to apologize for the lack of technical phrasing. I am trying to tech myself some things, but have become stuck.


I have a physical computer, that I want to use as a web server that will be accessible outside my local network. I have already installed Ubuntu 13.04 (raring ringtail), and have also install apache2, php and MySQL. I have already bought a domain name. My router has been configured for DMZ and the IP address of the web server is listed on the router.


I have already edited sites-available and also created a symbolic link from sites-enabled. At this stage however, I still cannot see the server from outside my network. I have already install shorewall and allowed ports 80 & 22.


Can anyone give me some advice where to go or what to do next. If this post seems vague, it's only because I am not sure what else to offer, but if anyone is willing and able to help, please feel free to ask whatever questions you need to help diagnose the problem. I am guessing it's a simple step or two I have left out.

Thanks 
Rob

---

### Post by ian-weisser on 2013-11-02
Is your domain name pointing to the correct IP address for your router?
Try the command **host your.domain.name**
```
$ host www.example.com
www.example.com has address 93.184.216.119
www.example.com has IPv6 address 2606:2800:220:6d:26bf:1447:1097:aa7
```

Does your router actually have the IP address that you think it does?

---

### Post by vangend.robert on 2013-11-03
Probably not, but in truth I don't know where to change that. In fact, I am not even sure what IP my router is supposed to have.

I have changed the port forwarding rules in the router so that "Webserver" & "IPSEC LPT2" are applied. Both of these rules are associated with the IP of my internal server machine. 

I ran "host www.vizmec.com" as you suggested and the result is:
[www.vizmec.com](www.vizmec.com) is an alias for vizmec.com.
vizmec.com has address 50.63.202.62
;; connection timed out; no servers could be reached

I will scratch around, and see what else I can find.

Any more input / suggestions would be most welcome.

---

### Post by ian-weisser on 2013-11-03
You can easily find your router's IP with several commands. For example: [B]wget -q -O - [http://www.icanhazip.com](http://www.icanhazip.com)
[/B]Does that match 50.63.202.62?

Does your ISP provide you a static IP address (never changes) or a dynamic IP address (frequently changes)?
If static, then your IP should never change.
If dynamic, do you have a dynamic dns (ddns) provider? Or is your DNS provider handling that for you?
If dynamic, did you install a ddns client recommended by the ddns provider?

Progress, step by step.

---

