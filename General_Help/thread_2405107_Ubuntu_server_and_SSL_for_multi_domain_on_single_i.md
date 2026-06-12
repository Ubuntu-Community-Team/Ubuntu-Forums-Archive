---
title: "Ubuntu server and SSL for multi domain on single ip"
date: 2018-11-01
forum: General Help
---

### Post by Adrian_Padilla on 2018-11-01
i have read some information of SSL certs that cover multiple domains on a single ip address... 

my question is are these less protected than regular SSL certs?

and can I use something like this on my server that I have in my office? and still, be protected like one that let's say GoDaddy has in their COLO? 

and lastly, would this be something that would be feasible for a newbie to install and set up

Thank you so much for your time and help in my quest for information

Adrian

---

### Post by TheFu on 2018-11-02
SSL doesn't provide security.  It just encrypts data between 2 points, provided neither side has already been compromised. It is possible to MiTM the traffic by modifying DNS and setting up a clone website/web-app that forwards requests to the real site.

The encryption used for most public-facing SSL certs is fine for most common uses, but only you can decide if it is sufficient protection for your needs.  The encryption used by any paid cert isn't any better than what you can get from Let's Encrypt free certificates. What the paid vendors provide is that some sort of validation was performed.  In reality, anyone can get a cert for a new domain without much hassle.  It is only the high-validation certs which cost 10x more than normal certs where the validation of the person and company are probably useful.

IMHO.

I don't trust HTTPS for any of my web-apps.  We require the use of a VPN to access most of them.  For our public-facing websites, there isn't any reason to add SSL, except to make it a tiny bit harder for the content to be modified by anyone. That hasn't been a problem anywhere that I know, except places that usually censor content already and have been caught doing it.  If you want better internet security to things you host, use a VPN.

Can a newbie install a cert?  Depends. Impossible to say.  I'd be more afraid they'd setup an insecure service and be hacked but wouldn't know for years.  Having an SSL cert doesn't do anything for system security.

---

