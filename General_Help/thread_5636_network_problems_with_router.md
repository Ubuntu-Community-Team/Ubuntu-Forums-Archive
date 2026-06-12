---
title: "network problems with router"
date: 2004-11-20
forum: General Help
---

### Post by osiris_22 on 2004-11-20
Ok my friend.. just installed ubuntu.. and if he connectst directly from his cable modem he gets a connection.. but if he connects his router to his nic he dont get a connection... so its cable modem to router to nic...***** and no connection.. any fixes?

osiris :neutral:

---

### Post by shad0w on 2004-11-20
[QUOTE=osiris_22]Ok my friend.. just installed ubuntu.. and if he connectst directly from his cable modem he gets a connection.. but if he connects his router to his nic he dont get a connection... so its cable modem to router to nic...***** and no connection.. any fixes?

osiris :neutral:[/QUOTE]
 Your gonna have to be a bit more descriptive. What kind of router does he have and how is he connecting it to his computer?

---

### Post by osiris_22 on 2004-11-20
Hes using a compusa router.. and hes connection to His ethernet card... via cable internet....

---

### Post by Rancoras on 2004-11-20
Ok, there's too many variables here.  Are you saying the router won't connect to the internet or he can't access his router from his computer?  You really need to go into more detail when you post.

---

### Post by osiris_22 on 2004-11-20
OK when hes using his router.. he cant connect to the internet.. when he dont use his router he can connect to the internet.... but he has to use the router because thre are other people in the house.......

---

### Post by Rancoras on 2004-11-20
It sounds to me like the ethernet card in his machine is working fine, otherwise he wouldn't be able to connect without the router.  Now I suspect the router.  Can he access the router's configuration from his machine?  Has the router ever worked before or is it brand new?

---

### Post by unikum on 2004-11-20
I have some problems with my home network too. My comp is connected to a router and then the router to the adsl-modem. Everytime i reboot i have to change dnsservers from 192.168.0.1 (router) to my isp's. If not it takes 3-5 minutes for firefox to resolv host. I have tried both to do this with networktool under program->system (i think thats the name, i use swedish language) and manually edit resolv.conf. But still default after reboot is 192.168.0.1.  :|  any suggestions?
In windows it works with default settings, why not in linux?

---

### Post by osiris_22 on 2004-11-20
yeah.. His router works fine in windows.. umm yes he went in to his routers settings wile in linux.. and turned off his firewall and did the whole dmz mode thing.. and set it to be an gateway or soemthing like that..... its just he cant get any connection at all.. its wierd.. my router dont do that to me at all.. and i have a microsoft router go figure lol...

osiris

---

### Post by stoneguy on 2004-11-20
Are we talking plain router, or is it a firewall/router like an SMC (don't know what brands are found in Europe) ?

If the latter, you put the DNS in when you set the box up. Its NAT capability will deal with the rest.

---

### Post by osiris_22 on 2004-11-20
can you put its dns in after you have ubuntu installed????

osiris

---

### Post by osiris_22 on 2004-11-20
well it dont matter now he fried his nix hard drive lmao..... hes reinstalling on another hard drive... them damned dells... 

osiris

---

### Post by Rancoras on 2004-11-20
He's saying that the ISP's DNS should go in the router.  That's how mine is set up and everything works fine.  

Does your friend's router show that the internet connection is up?  If so then try pinging [www.yahoo.com](www.yahoo.com) in a terminal.  If it fails to resolve the name then DNS may be your friend's problem as well.  You can check in Computer > System Configuration > Networking to check the DNS.  On the DNS tab, make sure that the router's IP is there for the DNS.  Then make sure that the ISP's DNS server is set in the router's config area.

---

### Post by arctic on 2004-11-21
there is a simple answer to this problem, but it took me ages to find the solution. 

here it is:
install with apt-get the following packages:

resolvconf
pump
dnsmasq

in case apt-get times out, retry, but this time open a new tab and ping the mirror. 
this worked on my and many other router-based boxes.
good luck. :)

---

