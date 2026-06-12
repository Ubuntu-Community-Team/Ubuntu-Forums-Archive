---
title: "DNS Records Configuration - Email Going Straight to Spam Box???"
date: 2020-10-18
forum: General Help
---

### Post by aaronesteban on 2020-10-18
I know that in order to hit the inbox, the main DNS records need to be properly set up. These are the main DNS records that every mail delivery system should have for their domain:


- TLS
- A
- MX
- DKIM
- SPF
- DMARC
- rPTR


The ones that I mainly need help with configuring right now are the following records:


MX, DKIM, & SPF.


I have iRedMail installed on my domain at:
aaronsnewsletters dot com


What exactly should I set for the MX records if I set my main mail server to mail.aaronsnewsletters dot com?


Am I supposed to set the MX records for the root/apex of the domain or do I set them to aim at the "mail.aaronsnewsletters dot com"?


Also, what about the DKIM & SPF?


Am I supposed to try pointing at the root/apex or the subdomain with the "mail."?


Any support is greatly appreciated.

---

### Post by TheFu on 2020-10-19
The MX looks fine to me.
The SPF looks fine to me.
I don't use DKIM.

TLS has always been automatic for postfix. A few years ago, I made it mandatory for all connections. My email server doesn't have any 3rd party cert. It is using a self-signed on.

What you call the 3rd level hostname is completely up to you.  mail.example.com .... the "mail" part can be anything you like, provided it is consistent with the other DNS records. The actual hostname doesn't need to match the MX record ... the DNS record for that MX just needs to point at the correct IP.

---

