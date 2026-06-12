---
title: "LAMP Server - cannot see web page."
date: 2007-05-18
forum: General Help
---

### Post by Titus A Duxass on 2007-05-18
Using Dapper, I have done a LAMP install.
I have created a directory "www" and amended  the document root so that it reads home/titus/www.

I have set up a dns with easydns and ran ez-ipupdate which says that it was successful.

However when I try and access the web site I get:

Firefox - The page isn't redirecting properly

Konqueror - An error occurred while loading [http://www.caracot.com:](http://www.caracot.com:)
Found a cyclic link in [http://www.caracot.com](http://www.caracot.com).

I can see it locally with 192.168.1.71

There was a thread where someone had similar problems but I cannot find it.

Has anyone got any pointers?

---

### Post by Titus A Duxass on 2007-05-19
Okay, this time I did a clean install with a Feisty CD and selected DNS and LAMP.

Again I can see it locally.

Again I get the problems with cyclic links or not redirecting.

I am obviously doing something wrong.

---

### Post by Stemp on 2007-05-19
I think there is a problem with your dns redirection.
When «Pinging» [www.caracot.com](www.caracot.com), the ip adress given direct you to Direct Domain with this message : The countrycode of your domain is unknown.
If you know your ip adress, try to acces to your home site with it.

---

### Post by az on 2007-05-19
Does your isp block port 80?

---

### Post by Titus A Duxass on 2007-05-19
Does my ISP block port 80?

I do not know, I am with Deutsche Telekom and have a flat call and surf paket.

I am trawling through their website (which is huge and in German) to find out.

---

### Post by Stemp on 2007-05-19
Do you know your ip adress ? try using it in Firefox, Epiphany, Konqueror etc...
You'll see if it's a dns problem or a LAMP configuration problem

---

### Post by Titus A Duxass on 2007-05-20
Okay,
According to Deutsche Telekom:
Hinweise bei Nutzung von Router/Firewall

      Freigeschaltete Ports (die Einstellung muss in manchen Routern/Firewalls manuell erfolgen):
      UDP (out): Ports 5060, 30000-30005, 3478, 3479
      UDP (in): Ports 5070, 30000-30005, 3478, 3479
      TCP (out): Port 80

      Nicht geeignet sind Router, die symmetrisches NAT einsetzen.

So it looks like my port 80 is free.

Going to dnsreport.com tells me that my IP is 217.111.100.210 with the following nameservers:

server1-ns1.udagdns.net. [62.146.28.82] [TTL=172800] [*E]
server1-ns2.udagdns.net. [62.146.33.101] [TTL=172800] [*E]
server1-ns3.udagdns.net. [62.146.33.102] [TTL=172800] [*E]
[These were obtained from c.gtld-servers.net]

At cqcounter.com it gives me the following information for my IP:

a. ISP = Colt Telekom Gmbh
b. Organisation = United Domains AG

Now this does not click with me, I have set-up a Dynamic DNS with easyDNS.
The print out from EasyDNS states that their nameservers are ns1.easyDNS.com with ip 216.220.40.243, etc.

So is something amiss with my DNS service?

---

### Post by az on 2007-05-20
> **Titus A Duxass said:**
> 

server1-ns1.udagdns.net. [62.146.28.82] [TTL=172800] [*E]
server1-ns2.udagdns.net. [62.146.33.101] [TTL=172800] [*E]
server1-ns3.udagdns.net. [62.146.33.102] [TTL=172800] [*E]
[These were obtained from c.gtld-servers.net]

At cqcounter.com it gives me the following information for my IP:

a. ISP = Colt Telekom Gmbh
b. Organisation = United Domains AG

Now this does not click with me, I have set-up a Dynamic DNS with easyDNS.
The print out from EasyDNS states that their nameservers are ns1.easyDNS.com with ip 216.220.40.243, etc.

So is something amiss with my DNS service?

With dynamic DNS, you have more than one DNS pointing to your IP address.  When you find your ip address, what happens when you visit that page?  

Like, if your router says that your external address is 123.123.123.123, what happens if you visit that address in your web browser?  What about a friend from outside your home?

If you can establish that you can serve pages to the outside, then you can fix your dynamic dns configuration.
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by Titus A Duxass on 2007-05-20
I think my IP address is 217.111.100.210, that is the result of pinging [www.caracot.com](www.caracot.com).

Entering 217.111.100.210 in a browser takes me to United Domains and gives the "The countrycode of your domain is unknown" failure.

During the boot process everything appears to start okay (bind, mysql, etc.).

Dmesg gives no failures or problems

---

### Post by Stemp on 2007-05-20
Ok first find you IP Adress : [http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/) (by example)
Try [http://localhost/](http://localhost/) to see if your LAMP is ok

---

### Post by Titus A Duxass on 2007-05-21
Thanks for that, I will try them at home tonight.

I have just tried going to my web site through my W2K machine at work, I get a different failure with windows:

Fatal error: Unknown: Failed opening required '/usr/local/apache2/htdocs/udag_redir/udag-redir.php' (include_path='.:/mnt/webspace/00/4553/php_includes') in Unknown on line 0

---

