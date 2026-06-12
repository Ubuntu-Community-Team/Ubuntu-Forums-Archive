---
title: "Postfix issue sending email to domain on localhost"
date: 2014-09-15
forum: General Help
---

### Post by Bob_OHara on 2014-09-15
Hi

Here's the issue. We installed Zpanel on a Ubuntu OS and it now manages and hosts all our domains. We also installed Postfix for email. The issue arises when a domain hosted out the new server uses another host for email. Instead of looking outside the server for MX postfix assumes it is to be sent locally and bounces it back when it can't find the address. This even though in the DNS records in Zpanel MX record for that domain is specified properly. Found this command:

/usr/local/psa/bin/domain --update example.com -mail_service false

But when I try running it I get to such directory. Can anyone provide any insight?

Bob

---

### Post by SeijiSensei on 2014-09-15
I'd start by reading this: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination)

---

### Post by lisati on 2014-09-15
> **SeijiSensei said:**
> I'd start by reading this: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination)

+1 for the suggestion. 

Postfix needs to know about *all* the domain(s) it is responsible for, otherwise it won't know what to do with email that is destined for a locally hosted account.

---

