---
title: "HTTPS set up problem 20.04"
date: 2022-12-02
forum: General Help
---

### Post by ozstar on 2022-12-02
Hi,

I have just set up a SSL Certificate and it was successfully installed.

On testing at the ssllab.com site, I got this message Assessment failed: Unable to connect to the server

I have set it so it redirects http to https and as checked that I have allowed 80 and 443 through ufw.

When I use the address say, mysite.com or [http://mysite.com](http://mysite.com) or [https://mysite](https://mysite) they all resolve at my router. 
They don't go through it to the site via 443 or 80.

It worked fine before I told it to redirect to the https:// address so.

Any ideas please to get it working.

EDIT:  I just checked port forward on the router and 80 is okay but 443 wasn't.

I tried to use it but got message can't use it as..

Port is used by router for HTTPS

How do I get around this.  It is a Netcomm NF18 MESH.

EDIT:  Did a    sudo netstat -ntupl | grep :443  and got  the following but not sure what it means.

> tcp6       0      0 :::443                  :::*                    LISTEN      615/apache2  

Should my virtual host .conf file have 443 in it as well as *80 ?

---

### Post by The Cog on 2022-12-03
What do you mean by "they all resolve at my router"? 
Try the command **[FONT=Courier New]host mysite.com[/FONT]** - from here it resolves to 64.136.20.67.

That netstat command lists all the listening tcp and udp ports on whichever box you ran it on. You passed that through grep which searched for a line containing :443 . That line says that apache2 (a web server) is listening on TCP port 443 on all addresses (both IPv4 and IPv6). So whatever box you ran it on is listening for incoming calls (though it might have a firewall interfering with the connections).

---

### Post by ozstar on 2022-12-03
[https://ibb.co/4ZpTmh8](https://ibb.co/4ZpTmh8)

Hi,
Thanks for the  help. 
What seems to happen is the router which won't let me add 443 to the forwaders  is stopping any request to show the http: and https site that I got the ssl certificate for.

In the certificate application it gave the option  to redirect all http calls to https.

That is what I wanted but then I found the router wouldn't  let me add 443. Now the url requests
stop at the router admin login page which is the gateway all  incoming request have to pass tgrough t o get to the server with it's apache conf files.

I need a command or something to tell the certificate script  to stop redirecting http to the not working https but no [IMG]https://ibb.co/4ZpTmh8[/IMG]matter what I look for, I can't  see what to do.


I have notified Let's Encrypt in the hope they can tell me what to do  or somehow change the  script  at their end.

I am still trying to work out what the router means when it says it is using  443.

EDIT:

I looked in the router to see ant reference to 443 and why it says it is set aside for http: and this screenshot is all I found that mentions 443 in the router admin NF18MESH Netcomm.

---

### Post by The Cog on 2022-12-05
Are you trying to connect into the webserver from the internet? If so, and if the router is listening on 443 for its own administration, then it will not be able to forward 443 anywhere else. It also means that the router's administration is open to the internet. You might be able to disable remote administration to free the port up for forwarding. Othewise you will have to forward a different port instead.

---

### Post by ActionParsnip on 2022-12-05
Try rebooting the router, may help. I've had some routers refuse to set what I wanted until I rebooted them

---

### Post by ozstar on 2022-12-06
> **The Cog said:**
> Are you trying to connect into the webserver from the internet? If so, and if the router is listening on 443 for its own administration, then it will not be able to forward 443 anywhere else. It also means that the router's administration is open to the internet. You might be able to disable remote administration to free the port up for forwarding. Othewise you will have to forward a different port instead.

Thank you.  Yes but I wonder what ramifications there could be by disabling 443.  Not sure what else is relying on it being locked.  There is a place in the 'Access' area of the [COLOR=#000000]Netcomm NF18 MESH where I can enable any of the ports including 443.

EDIT:

OM further looking saw it was to enable it for WAN which is not what I want.
[/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291387&stc=1[/IMG]

---

### Post by The Cog on 2022-12-07
I found their manual online. Nice router. 
[https://support.netcommwireless.com/api/Media/Document/c44992af-4721-4c7c-abb2-1030daa19dc8?Product=NF18MESH%20User%20Guide.pdf](https://support.netcommwireless.com/api/Media/Document/c44992af-4721-4c7c-abb2-1030daa19dc8?Product=NF18MESH%20User%20Guide.pdf)

The page you screenshot above is for configuring access to services on the router itself. I think that's what you want, as shown in your post, so the router does not offer any of its services to users connecting to it from the internet. 

I guess the port forwarding you need to configure would be on page 49/50 of the manual I linked here. I'm guessing, but:
Use interface: WAN, Service name: mysite, LAN Loopback: Enable, 
Server IP address: Whatever the inside address of your webserver is (you don't say but I guess 192.168.something),
External start port: 443, External end port: 443, Protocol: TCP, Internal Start port: blank, Internal End port: blank

However, the router is still offering its own management on port 443. If it still claims port 443 is in use, you may be able to move its management to another port by changing 443 to something else on the page you posted (might work, probably needs a reboot). Remember I don't know this router, I'm guessing.

---

### Post by ozstar on 2022-12-10
Thank you The Cog. Really appreciate your help. I will take a look asap to see how that all works out. Hope so !  
It sure is tricky with so far no definitive answer no matter where I ask, but maybe your guessing is right.. Woof :-)

---

### Post by TheFu on 2022-12-10
Doubt I can help, since this seems to be an issue with a specific router.
Some routers have "security settings" which prevent access to internal forwarded IPs from the same LAN.  
It is possible that either the ISP has setup 443 for remote management of your router or that from inside, port 443/tcp is the router admin page, so any requests from the LAN will be sent there, not forwarded to the real system.

However, I use let's encrypt and have about 20 different certs that were renewed earlier this week. All worked perfectly, so I don't think it is an issue with Linux or LE.  I've been using the acme.sh tool to create and renew certs. I use multiple modes since some of my websites are "static" and others go through a reverse proxy which terminates the TLS connections before forwarding traffic to the back-end servers. Some are load balanced.

Also, if you are blocking any parts of the internet, Let's Encrypt may refuse to generate certs. They have a belief that the entire world should be able to access your website and check using at least 3 different locations BEFORE they will issue any certs.  They've been doing this a few years after a few years where they didn't have these mandates, just warnings.  When it became mandatory, I had a week to figure it out before my certs expired, so I looked at logs on the router, the reverse proxy, firewalls, and on each web-app system.  I was blocking specific regions of the world based on which countries had launched attacks against my servers and some added subnets in other countries that also launched attacks.  Today, I'm blocking about 8000 subnets on the IPv4 internet, 100% of IPv6 because I'm not ready for it and don't think I can secure my systems.  However, for the 2 minutes every 77 days that it takes to renew the LE certs, I remove all firewall blocking. When the certs are renewed, I enable those blocks again.

It all gets confusing.  Check the logs, everywhere.

---

### Post by ozstar on 2022-12-10
Wow you sure have had some work getting dodging the bullets with your system.  I know my prob is with the router not Linux or Let's Encrypt as that went flawless fore me. Problem started when router refused to port forward 443. I'm waiting on word from the router manufacturer to advise what 4433 is actually doing and if/how I can get around to using it.
I know I could change the ssl to another port although of every place I've looked at, I still can't find a definitive way to do it.
Some seem to find it okay for the initial page but when going to another page and when returning, get back to 443 again. Confusing fo sho'  :-)

---

### Post by TheFu on 2022-12-11
443/tcp is the normal, expected port, but any port can be used.  Some residential ISPs block popular inbound network connections on popular ports, like 25, 20, 21, 22, 80, 443, 8443, 8080, and a few others, since their contract says that you won't run any servers on the connection.  

You can use any port you like, but Let's Encrypt wants to validate only specific ports when using their web-validation modes.  You can also enter a DNS txt record with the  LE challenge to prove you own the domain.  Some people do it that way.

As for expecting help from a router company, I have doubts they will be helpful.  The big guys expect you to get professionally trained and the little guys expect you'll read the manual which will be pretty clear for how to forward ports and list "security features" which may prevent certain types of connections from working - Like a LAN connection to the public IP is commonly blocked in consumer routers as a security feature.  Different routers call this "feature" different things, so reading the 20 page manual will probably be needed.

Google found this thread: [https://forums.whirlpool.net.au/archive/3kvlwz89](https://forums.whirlpool.net.au/archive/3kvlwz89) that describes the same problem and a few solutions, specific to Aussie DSL services.  First question, did you opt out of CG-NAT?

---

