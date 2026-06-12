---
title: "[SOLVED] How to make my computer SSH-able from another network"
date: 2007-11-16
forum: General Help
---

### Post by HokeyFry on 2007-11-16
Alright, I have a computer that I would like to be able to access via the internet. The only thing is is that I am behind a router, and I have no idea how to, for example, SSH into this machine from another network. I have SSHed and SFTPed into the computer from on the network before, so I just need to know how to access it using an IP address from outside the network. Thanks for any help in advance.

---

### Post by geirha on 2007-11-16
You need to log into your router and forward port 22 to your machine. Then you can ssh in using the external ip. [http://portforward.com](http://portforward.com) has guides on how to port forward for specific routers. Chances are you'll find a guide for your router there.

---

### Post by mattack on 2007-11-16
You'll also need to know the external IP address of your router
You might want to look into a dynamic DNS service as well, like DynDNS.com. You can set up a program on your computer or possibly your router to update the dyndns servers with your routers external IP address, which can change depending on your ISP, connection type, etc... That way you can remember a hostname like mycoolubuntubox.home-linux.org, instead of keeping up with what your IP address is.

---

### Post by HokeyFry on 2007-11-17
Alright, one more question. My external IP only updates when I hard reset my modem by unplugging it correct?

---

### Post by Craigus on 2007-11-17
> My external IP only updates when I hard reset my modem by unplugging it correct?

Maybe. That depends on how your ISP does things. That is certainly not the case for every ISP, including mine. It is easy to set up a free DynDNS account anyway, and then you can be sure that it will always work.

[http://www.dyndns.com/services/dns/dyndns/]("http://www.dyndns.com/services/dns/dyndns/")

---

### Post by HokeyFry on 2007-11-18
Ok, so I set up my dyndns account and it seems to be working fine at this point. Now, the only problem is what happens when my external IP changes (i.e. on reboot of the modem)? mattack says there is a way to have this auto update the IP on dyndns.com, but I don't know if its got anything to do with dyndns or if i have to write something to update the IPon my own. Any ideas?

---

### Post by geirha on 2007-11-18
Use ipcheck or ddclient to have your computer update the ip-adress regularly. There's a simple guide here for feisty, it should be the same in gutsy. [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_dynamic_IP_addressing_for_your_host_using_the_free_DynDNS_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_dynamic_IP_addressing_for_your_host_using_the_free_DynDNS_service)

---

### Post by HokeyFry on 2007-11-18
Thanks, that guide really helped. I used ipcheck to do this. Thanks a bunch everyone!

---

### Post by mattack on 2007-11-20
> **HokeyFry said:**
> Ok, so I set up my dyndns account and it seems to be working fine at this point. Now, the only problem is what happens when my external IP changes (i.e. on reboot of the modem)? mattack says there is a way to have this auto update the IP on dyndns.com, but I don't know if its got anything to do with dyndns or if i have to write something to update the IPon my own. Any ideas?

Some routers have this capability built in too. I have a crappy D-Link that updates my DynDNS for me when the external IP changes, rather than using precious CPU cycles of my 7 year old computer. :)

---

### Post by HokeyFry on 2007-11-20
lol yeah i found that option but the only thing is it seems i have to manually update it if the IP changes =\

if it goes down for that reason though its nothing a phone call to my pops wont fix:popcorn:

---

