---
title: "Need help with postfix"
date: 2020-07-27
forum: General Help
---

### Post by kladizkov on 2020-07-27
We already have postfix running for last 10 years. We need to do some restrictions on it.

We have a domain abccompany.com. We need to setup email server where we need to restrict sending of emails within our two domain for most users. For example, [email]everyone@abccompany.com[/email] can send to [email]any@abccompany.com[/email]  and [email]any@xyzcompany.com[/email], but not to any other domains like *@gmail.com, *@yahoo.com etc. But same time, a few email users should be able to send to any outside domains ( like gmail or any domain for that matter ). What approach should I take for this?


If any one wants to send a mail to outside domain, they can prefix #personal# in the subject and it will wait for some approval from admins. Is this possible using postfix?

---

### Post by TheFu on 2020-07-27
I don't know answers, but here's how I'd attempt it.  

[LIST=1]
[*]Setup 2 different postfix VMs.  
[*]A only for internal emails (no way to use it for any outbound email, ever) and 
[*]B for general, anywhere, emails.
[/LIST]
Postfix is very light and easily runs in an lxd container which should be under 500MB each, so there isn't a need to allocate whole servers, just need an IP for each.

[http://www.postfix.org/transport.5.html](http://www.postfix.org/transport.5.html)
[http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html)

Sorry I'm not more help. We only use a tiny postfix server as an email gateway (in/out) to block 95% of the inbound spam that fail simple checks and prevent outbound that doesn't go through allowed, specific, internal email servers. 

I haven't any clue how to have "personal" emails sent external only using the same infra and would never even entertain that capability. It would be abused.  Most people have phones and would use them for personal email needs. There are some other options, like having some separate ISP-connected PCs for personal use in a common area. Lock that down like a public library or primary school would.  Perhaps running something like ChromiumOS, so they are secure, have excellent web browsers, and can't be abused by Windows software, while still having internet and webmail access for personal use during breaks.  Lots of methods exist to solve these needs that don't require a complex postfix setup.

As part of a full security architecture, there are many more details to prevent desktops from having any direct internet access.

---

### Post by SeijiSensei on 2020-07-27
I'd start by reading this at least twice: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

In particular, you probably want to read up on smtpd_sender_restrictions and [http://www.postfix.org/access.5.html](http://www.postfix.org/access.5.html).

---

