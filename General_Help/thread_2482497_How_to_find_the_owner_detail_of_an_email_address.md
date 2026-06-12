---
title: "How to find the owner detail of an email address"
date: 2023-01-02
forum: General Help
---

### Post by satimis on 2023-01-02
Hi all,

Would it be possible to find the owner and other details of an email address?

Thanks

Regards

---

### Post by TheFu on 2023-01-02
> **satimis said:**
> Hi all,

Would it be possible to find the owner and other details of an email address?

Thanks

Regards

Not really.

Depends on how honest they are.  I routinely send messages from 'God@domain.com' to family as a joke.  The FROM can be anything, provided it is in the correct format. It can even be empty.  Validation of the domain CAN be required by different servers along the way, but not the FROM.

SFP, DKIM and DMARC are protocols added as optional parts to the SMTP protocol (SMPT is what server-to-server message transfers use).  These can be used to validate that the sending email address is actually part of the sending email server's managed domains.  

> SPF (Sender Policy Framework), DKIM (DomainKeys Identified Mail), and DMARC (Domain-based Message Authentication, Reporting and Conformance) are email authentication protocols that are becoming increasingly necessary to run a working email server. 

SPF can be run in 3 modes.  They are basically, strict, optional and off.  SPF is implemented in DNS TXT records and says in the DNS record for a specific domain, which smtp server IPs can be used to send email for client email servers to block any domain email that arrives from any other IPs.  The email sender's admin would set this up.  All of these SMTP confidence extras can break email lists which have been working for decades.  I only have SPF setup due to the way my email server and gateways are setup for security.  I haven't looked into the DKIM and DMARC signing and don't plan to until my communications server version supports them easily and the messages traverse the email gateway unmolested.

It is up to the recipients email server to check that added information and choose if it makes sense to allow any specific the message or not.  

But what you can do is trace the email servers involved. That's in the headers for each server hop made from the sender's email server to the recipients email server.  Spammers will often stand up a temporary email server, blast nearly 1M messages before they get shutdown.

Think of email as a postcard.
* Only the "TO" address matters.
* FROM can be anything and is never validated.
* Like postcards, anyone between the sender and recipient can read everything in the email, just like the postal workers picking up or delivering or anywhere along the way can read the postcard.

If you want to ensure an email is valid, you'll want to use PGP or GPG encrypted and signed messages AFTER you validate the cryptographic signature.  This can be handled either as just a way to sign the full, unencrypted, message to ensure the sender is actually the sender or as a way to encrypt the message between 2 parties and ensure that not only is the sender the correct person, but that the message can only be opened/decrypted by the target recipient.

---

### Post by satimis on 2023-01-03
> **TheFu said:**
> Not really.

Depends on how honest they are.  I routinely send messages from 'God@domain.com' to family as a joke.  The FROM can be anything, provided it is in the correct format. It can even be empty.  Validation of the domain CAN be required by different servers along the way, but not the FROM.

SFP, DKIM and DMARC are protocols added as optional parts to the SMTP protocol (SMPT is what server-to-server message transfers use).  These can be used to validate that the sending email address is actually part of the sending email server's managed domains.  
......
....
Hi TheFu,

Lot of thanks for your detailed information and explanation.

Occasionally I received email, say for example, from [email]AAA@domainA.com[/email].  Actually it was sent from address [email]BBB@domainB.com[/email].  The later email address was hidden.

Regards

---

### Post by HermanAB on 2023-01-03
Look at the email headers.  That will give you some idea of where it came from.  Most mail readers have a way to display the normally hidden headers.

---

### Post by TheFu on 2023-01-03
> **satimis said:**
> Hi TheFu,

Lot of thanks for your detailed information and explanation.

Occasionally I received email, say for example, from [email]AAA@domainA.com[/email].  Actually it was sent from address [email]BBB@domainB.com[/email].  The later email address was hidden.

Regards

I fear you missed my point.  The FROM can be anything the other person typed in, only the domainB.com part "may" be restricted to be valid.  There is another SMTP header, "REPLY-TO", which can be anything and doesn't get validated.  In general, if the FROM and the REPLY-TO are different, it is 
a) spam
b) from a huge corporation that doesn't really want any replies.

I have a 'no-reply@domain.com' address that I use to send messages from time to time.  Seems most people get the hint.

Normal people don't really understand email, nor do they really understand how much of it is based on people being nice.  If you want to have fun or just be nasty, there are all sorts of things that SMTP allows.  Effectively, there's no validation in the core protocol, just like with UDP.  Only the 'TO' address matters, since that would be the target. Same for UDP.

---

