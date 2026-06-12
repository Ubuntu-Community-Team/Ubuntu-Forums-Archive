---
title: "how can i host a email / web page from a godaddy registered domain name ?"
date: 2007-09-11
forum: General Help
---

### Post by kraymore on 2007-09-11
how can i host a email / web page from a godaddy registered domain name ?  

i am running feisty.  i found a tutorial on hosting apache2/mysql/phymyadmin/wordpress however it makes no mention of configuration and how to set it up to use a domain say, hosted at godaddy.com.  

would appreciate any advice

i realize this might be asking too much, though it would be useful for me to know how to do so being behind a linksys router.  i am also unaware of comcast blocks port 80.  worth a shot.

---

### Post by coggins on 2007-09-11
Not sure if I'm quite clear on the question, but here goes...

The GoDaddy name shouldn't make any difference at the server end.  It's merely a forwarding service.  So when your site is set up, just go to godaddy and put in the server IP address as the target for the forwarding.  There is an option to make this blind so people viewing the site only the see the godaddy domain.

For the behind the router thing,  I geuss you probably want to set up a DMZ for the web server.

---

### Post by hugdaba on 2008-06-03
> **kraymore said:**
> how can i host a email / web page from a godaddy registered domain name ?  

i am running feisty.  i found a tutorial on hosting apache2/mysql/phymyadmin/wordpress however it makes no mention of configuration and how to set it up to use a domain say, hosted at godaddy.com.  

would appreciate any advice

i realize this might be asking too much, though it would be useful for me to know how to do so being behind a linksys router.  i am also unaware of comcast blocks port 80.  worth a shot.

I am also wanting to know the same. I'm not too familiar with lixun or xubuntu/ubuntu for that matter. ive got all the mysqlserver and php "apted" in and installed, but as far as forwarding the domain to a box at home im almost certainly lost. (seems the nameservers or lack there of is the big problem) im using dyndns to overcome the no-static-ip issue, but as far as getting all that to a box again...i am lost lol. some pointers or light on the subject would much appreciated!

---

### Post by dfreer on 2008-06-03
The main thing you will want to figure out, before anything else, is whether it will be possible to host your own site at all. You will need to know whether your outgoing port 80 is blocked by your ISP. This is the steps I would take:

Install the apache server, and verify you can reach it from [http://127.0.0.1](http://127.0.0.1) or from another computer on your LAN. Give your server a static IP address on your LAN.

Open up your router configuration page, and make sure that the incoming port 80 on your router is forwarded to port 80 on your server.

Find out your current external IP address (the IP address the world can reach you from) by visiting [http://www.whatismyipaddress.com](http://www.whatismyipaddress.com)

Either call a friend who you trust can operate his/her internet browser, or check out a free proxy site (preferably both), give him/her/it your external IP address, and see if they can see your page. Another way to do this is to visit [http://www.canyouseeme.org](http://www.canyouseeme.org), but be careful this can give you a false positive sometimes (it could be actually seeing your router/ISP instead of your PC).

If this works, then the issue is just registering a domain name (preferably with a site that provides DNS services) and then pointing some DNS servers to your external IP address. I happen to like using dyndns to take care of everything (domain name registration, DNS servers, dynamic IP address updating), but you could use [http://freedns.afraid.org](http://freedns.afraid.org) or some such similiar site if you wish.

---

### Post by kraymore on 2008-06-04
I managed to be able to host my domain using the godaddy registrar.  i think they key to me doing it was using zoneedit.com i think its called, and using a script on my ubuntu box to query their server every so often, and the inputting some information from zoneedit into godaddy.  it worked alright.  setting up email services for my domain was a little too difficult for me, and the web that i could offer at home with comcast, just could not compare to what a decicated server could do.  i'm very sorry i do not remember the exact service that zoneedit offers that is needed to do it, but they have what you need.

<sorry i did not realize i was not adding new information to this post.  the reply notification that I was responding to was sent to my email>

---

