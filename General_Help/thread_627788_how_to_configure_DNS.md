---
title: "how to: configure DNS?"
date: 2007-11-30
forum: General Help
---

### Post by johnswb on 2007-11-30
I have one Ubuntu Server 7.10 that is running DHCP and 3 workstations that are getting there IP's from the server.  I am now trying to configure DNS so that my workstations can browse the internet.  I can hit google.com from my server but none of my workstation are able to.  I've installed Webmin which had made a lot of the configuration easy.  I am completely lost on the DNS part.  

Please help, I am will to start all over if I have too.

---

### Post by HermanAB on 2007-11-30
You can set up a DNS slave on the server, or you can simply point the workstations /etc/resolv.conf file to your ISP DNS servers.

---

### Post by johnswb on 2007-11-30
So... I only need a slave zone and point it to my ISP DNS servers?

I also get the following when I click on "Force Update" when editing the slave zone.  NDC command failed : rndc: 'reload' failed: no owner

PS. thank you for replying

---

### Post by NoWhereMan on 2007-12-01
resolv.conf will be probably reset on reboot: use **sudo network-admin**

---

### Post by johnswb on 2007-12-01
NoWhereMan you are correct....

Last night I gave up and just shut down my server and went to bed.  This morning after powering on the server all is good.  

HermanAB was correct as well.

I'm pointing DNs server to my IPS DNS servers and all is good.

Thanks guys

---

