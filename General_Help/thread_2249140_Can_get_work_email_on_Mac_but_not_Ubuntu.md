---
title: "Can get work email on Mac but not Ubuntu"
date: 2014-10-19
forum: General Help
---

### Post by Ditchdoc7893 on 2014-10-19
Hello all! 

This is an issue I've messed around with here and there, but never have come up with a viable solution and was wondering if any of you have any new ideas. Started bugging me after I was able to successfully get my work email to load up on a Mac. I figure surely by now there is a Ubuntu solution out there.

I recently updated my Macs to Yosemite. I was actually able to get the email client on the Mac to poll for my work emails. On Ubuntu, I've tried Thunderbird with DavMail as well as Evolution without any success. It just seems odd that Apple products and their email clients have no problem with the work MS Exchange server, but I cannot get get anything in Ubuntu to function correctly. 

Any suggestions/solutions? I plan to get with the IT guys at work this week to confirm settings, but this is really annoying. 

Thx in advance!

Ryan

---

### Post by TheFu on 2014-10-19
So ... Linux follows standards.  IMAP, POP3 and SMTP.  Ask your email admins which ports and connection settings to use for those protocols.  The standard answers would be 
* IMAPS = 993/tcp
* pop3s = 995/tcp
* SMTPS = 465/tcp

I've connected to MS-Exchange using the standards, but it is possible for the email admin to only support MSFT proprietary protocols. Some Linux email servers will connect, but I don't know if Thunderbird will. Evolution may - I dunno.

---

