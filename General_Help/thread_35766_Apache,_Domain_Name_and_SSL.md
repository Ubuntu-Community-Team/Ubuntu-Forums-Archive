---
title: "Apache, Domain Name and SSL"
date: 2005-05-20
forum: General Help
---

### Post by ExemplarUbuntu on 2005-05-20
Hi,

I'm sorry if this is a basic question but I've done some searching and can't dig up the answer.

I've installed Apache and managed to get access to the web page via the ip address but I need to know the url so that I can create ssl certificates.

I thought the url would be in the Ubuntu Network settings.

The only other difficulty has been trying to change the document root folder.

Peter

---

### Post by Zelut on 2005-05-20
If this is a page that you're running on your local box with apache you probably wont have a URL.  You'll be able to access it via the IP address but unless that IP has been registered with a DNS and assigned a URL (ie; ubuntu.com) you wont have one.

If you give me a bit I'm trying to find the name of the dynamic dns server I've used.  They can assign you a [www.server_name.homeip.xxx](www.server_name.homeip.xxx) which you can use as a URL to a static or dynamic IP.  This may be what you need, but I can't find the URL just yet.

EDIT:  [http://www.dyndns.org/](http://www.dyndns.org/)

---

### Post by ExemplarUbuntu on 2005-05-20
This is just for an intranet so I don't want to register a domain name.

From what I read on another thread I can't use the ip to create an SSL certificate it has to be the FQDN.

Is it really necessary to register the Domain just to do this ?

Peter

---

### Post by ExemplarUbuntu on 2005-05-31
BTTT

Does anyone know how to do this ?

---

