---
title: "Multiple Websites from Same Dynamic IP"
date: 2007-08-19
forum: General Help
---

### Post by JavaMonkey2006 on 2007-08-19
Hi Guys,
I have a quick question to ask, though this may not be strictly Ubuntu related but I was hoping that some of you could share your knowledge and provide with some information.

Basically I half host one website at the moment ([www.website1.co.uk](www.website1.co.uk)) on my home server. I have bought the domain name [www.website1.co.uk](www.website1.co.uk), there are a couple of html files on the providers servers, however when some one submits a request (say a search) the html form redirects the request to my home address which is a dynamic IP.  So I have setup a dynDNS name so that when a request is sent it is sent to the address of [http://website1.dyndns.co.uk:8080](http://website1.dyndns.co.uk:8080), this is all fine and works quite well.

The problem is that I have been asked by a friend to setup a new website and I was wondering if I could host it on the same server but mask the dyndns name somehow?

Basically if I buy a domain name [www.website2.co.uk](www.website2.co.uk), I will have to forward requests to [http://website1.dyndns.co.uk:8081](http://website1.dyndns.co.uk:8081) (or what ever port I use for the other site).  The problem of the users being able to see the other websites (website1) dyndns name in their address bar may come across a bit confusing for them.

Is there a way to mask this address so that it looks like its the original website name (no dyndns in address bar)?  Or am I completely going about this the wrong way?  Any help you could offer would be much appreciated.

I had thought about contacting the guys who host the main website and seeing if they could forward it onto my dyndns address, however they also host a pop email server and i need [email]myname@website1.co.uk[/email].  I did think about setting my own postfix server up, which I have done, however being a dynamic IP it is likely that my emails would get rejected at every turn.   Thought about relaying the emails through my ISP's smtp server, however I would rather not do this without their knowledge (and if they did know they would likely say... no).

Here is the configuration I am using:

Ubuntu Server 6.06
Apache Tomcat 6.0.8
DDClient
Port forwarding on router

---

### Post by HermanAB on 2007-08-19
You can do virtual hosting in Apache provided that each name resolves in DNS.  So your friend has to register a domain name with Godaddy.  Otherwise, you have to use separate ports.

Hope that helps.

Herman

---

