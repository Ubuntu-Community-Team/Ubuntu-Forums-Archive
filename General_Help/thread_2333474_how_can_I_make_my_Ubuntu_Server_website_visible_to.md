---
title: "how can I make my Ubuntu Server website visible to the world"
date: 2016-08-10
forum: General Help
---

### Post by Lukasz Tarkowski on 2016-08-10
how can I make my Ubuntu Server website visible to the world,  the Ubuntu Server page Apache it works in my house but it doesn't work anywhere else in the world

---

### Post by SeijiSensei on 2016-08-10
Here are two options:

1) Set up port forwarding on your router so that connections to its external port 80 are forwarded back to the server.  Your ISP may block or otherwise disable such connections since running servers usually violates the Terms of Service on residential accounts.  You'll need to set up a domain and point an A record at the router.  However all this only works well if your public IP address remains pretty static.  Otherwise you have to use kludgy DNS services that change your DNS records when your address changes.

2) Rent a virtual server at Amazon EC3 or Linode or a similar service and publish your website there.

---

### Post by dragonfly41 on 2016-08-10
*Provided that* your Internet Service Provider's terms of usage allows (your home account?) you could use dynamic IP address.

[http://dyn.com/dns/dyndns-pro-free-trial/](http://dyn.com/dns/dyndns-pro-free-trial/)

Search "dynamic IP" to look for others.

Some ISP's block ports such as 80 on home based servers so you might need to use a port such as 8080.

But usually you would host your server on a hosted service (i.e use your home server for development only).

[Later edit]

nitrous.io offers a good free trial service for testing server images.

---

### Post by dragonfly41 on 2016-08-10
This added link I archived some time ago. Might be useful for demos of apps on your home server ..

  ngrok.com

---

### Post by pqwoerituytrueiwoq on 2016-08-10
as [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") said port fowarding, i will add they may not block port 443 (the https protocol) assuming port 80 is blocked

there are free ddns providers like duckdns.org

---

### Post by vasa1 on 2016-08-10
@Lukasz Tarkowski, Would you please consider updating your profile information from "Ubuntu 11.10 Oneiric Ocelot" to whatever it is now? Thanks!

---

### Post by Lukasz Tarkowski on 2016-08-11
So what is a good free dns server, so that other people can see them and other wifi hot spots,  I will not be available Friday, and this weekend

---

### Post by Lukasz Tarkowski on 2016-08-11
So I found the services which one is good, This one [http://www.noip.com/free](http://www.noip.com/free) ? or this one [https://www.dynu.com/](https://www.dynu.com/) ?

---

### Post by 1clue on 2016-08-11
Depending on how much traffic you anticipate, generally home accounts have high bandwidth going toward the house and low bandwidth leaving. This is exactly the opposite of what you would want for a web server.

While I have never tried a dynamic dns, I understand that when your dhcp lease expires for your home account and you get issued a different IP, there can be an interruption of service since the dns will undoubtedly update sometime after that change.

If your intent is to host a simple page about your interests then it's possible to do so this way. My ISP does not restrict any ports either by contract or firewall. The only restriction is that home accounts have small outgoing bandwidth and large incoming bandwidth, and they don't give you a static ip unless you ask/pay for it. In my case it's about $10/month per static ip address.

---

### Post by mastablasta on 2016-08-18
interesting marketing methods.

here for statis IP all you need to do is request for it to be enabled.

after it's enabled they will gladly help you set up port forwarding in case documentation is not clear. i had to use their help when they replaced router and settings were totally different and named differently (very strange translations?!)

as for the bandwidth - i pay unlimited optical which should be 20 up /50 down. or maybe it is 50/50. in any case i can use the whole bandwidth however i please. on the other hand i limited server to max 5M/5M and i also limit other services i use to lower bandwidth. the only thing i left unlimited is internet browsing, various temporary game servers" and downloads. usually the issue is not the country network but anything from UK, USA. Germany and up to Paris works also as expected. makes sense i believe. 

in any case if you pay for the unlimited bandwidth, it means you can use it however you want.  so home server are nothingn unusual here. though if i am after a web or mail server i would rather have that done by the host. and i do use a host for that since they take care of all security, backups, spam filtering etc. for a really small yearly fee.

---

