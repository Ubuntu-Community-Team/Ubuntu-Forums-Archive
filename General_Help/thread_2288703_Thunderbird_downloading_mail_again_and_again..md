---
title: "Thunderbird downloading mail again and again."
date: 2015-07-29
forum: General Help
---

### Post by sandeep21 on 2015-07-29
Good day All,

My friends and I have five PCs with Ubuntu 14.04 LTS and Thunderbird 31.4.0 installed with at least seven email accounts configured in each of them. 

The email service provider is yahoo bizmail. (Our settings are pop based -> pop.bizmail.yahoo com port 465 and smtp.bizmail.yahoo.com port 995) Each account has inbox with size varying from 800 MB to 6 GB (I am not sure whether problem stated below is connected to size of email folders). 

The problem(s) we are facing are:

1. Every now and then same email is being downloaded again and again (we are told to keep Server Settings-> Leave messages on server unticked but that would make emails disappear from online yahoo server, and we would need it for future purpose)

2. Sometimes TB stops fetching mails and we need to close, restart and wait to download new mails again, sometimes repeating this step.

Can someone help. I have already been suggested to drop TB and go for Evolution. Any advice?

---

### Post by SeijiSensei on 2015-07-29
That's a common glitch that happens when you try leaving the mail on the server with POP3.  If the timestamps don't match up properly, you get all the mail again.  I ran a POP server for a client where the users were running Eudora and had this problem from time to time.

Can you switch to IMAP instead?  It's a much better protocol if you want to keep the mail on the server.

---

### Post by sandeep21 on 2015-07-31
Good day SeijiSensei,

Pleasure meeting you again and thanks for coming to rescue. I showed your solution to people but due to requirement to have a local copy of mails for immediate use (sometimes entire mails is sent as an attachment file to clients), we are not so sure about IMAP. Any other advise you have? the problem persists with mails getting downloaded repeatedly. Is our problem is connected to the fact that same account is configured in all the five PCs and sometime all the TBs "try" to pull the email together at the same time into their respective inboxes?

---

