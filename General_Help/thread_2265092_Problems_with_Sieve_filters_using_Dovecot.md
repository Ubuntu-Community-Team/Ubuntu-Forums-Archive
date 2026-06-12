---
title: "Problems with Sieve filters using Dovecot"
date: 2015-02-12
forum: General Help
---

### Post by terryit3 on 2015-02-12
First off I am using Ubuntu 14.04.1 with Dovecot and Postfix to run my mail server.
I have SpamAssassin installed and it appears to be working correctly. It marks my test spam messages with ****SPAM**** in the subject line.

I am having trouble getting my installation/configuration of dovecot-sieve to automatically move the marked messages to the users Junk folder.

I am using MailDir structure in Dovecot, not mbox.

I followed the guide at [https://rtcamp.com/tutorials/mail/server/sieve-filtering/](https://rtcamp.com/tutorials/mail/server/sieve-filtering/)  but it is filtering on Dovecot LMTP, but I am not using LMTP. 

Can anyone offer some assistance in getting it working on Dovecot IMAP? Hopefully I am asking that correctly. I'm sick today and cannot think straight.

Thanks very much!

---

### Post by terryit3 on 2015-02-12
I found a way to accomplish what I needed without using Sieve. I just used the message filters in RoundCube and Squirrelmail.

---

