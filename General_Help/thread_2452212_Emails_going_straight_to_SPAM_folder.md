---
title: "Emails going straight to SPAM folder"
date: 2020-10-18
forum: General Help
---

### Post by aaronesteban on 2020-10-18
So I've set up my own mail server with iRedMail on Ubuntu (20.4 I believe) to host my virtual boxes for my domain email accounts that are created as the admin, and Roundcube to send and receive the emails.


I've already set up my DNS records, SPF, DKIM, & DMARC, but when I try to send emails from my mail server/SMTP server, ALL messages keep going straight to the SPAM folders of my gmail recipients.


According to mxtoolbox, mail-tester, and several other sites, all of my records have been properly configured for my website. Mail-tester dot com even shows that I'm getting a 10/10 rating as far as passing spam filters goes.


So what else can I do to hit the inbox or what else could the issue be? 


The domain that I'm referring to (that should have the correct DNS and other records set up) is:


aaronsnewsletters dot com


Maybe someone can do a quick test against the site to see the records and let me know what you think.


Any support is greatly appreciated.

---

### Post by TheFu on 2020-10-19
Reverse DNS doesn't seem to be setup. Looks like DO owns that IP. While not strictly required, it is something that spam filters will consider.  For a new domain, I suppose gmail is taking the "assume spam first, until proven otherwise" stance. So, until the users help gmail learn that it isn't spam, I don't know what else to say.

This assumes it isn't actually spammy and is full of spammy links, advertising, etc.  Does every email have the legally required "how to unsubscribe" footer?

---

