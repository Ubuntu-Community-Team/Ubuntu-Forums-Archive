---
title: "Integrate mail-delivery-stack (ie postfix and dovecot with active directory)"
date: 2014-05-28
forum: General Help
---

### Post by DieEier on 2014-05-28
Hi all

I need some help.
The plan:

Set up ubuntu mail server - done
Use server 2003 active directory as source of users and to authenticate -- STUCK
migrate all user email from old mail server ( running slackware 12.1.0 , sendmail 8.14.2, fetchmail 6.3.20) -- will do as soon as auth prob solved.

Where I am now:

I set this server up with ad auth for SQUID 3.2. works well

I can kinit users and can wbinfo -t as well as log users in with wbinfo.

Kerberos seems ok for squid
NTLM auth seems ok for squid

I am having trouble getting postfix 2.10.2 and dovecot 2.1.7 configured to use tha AD as well.

Could anyone point me in the right direction. Google does not seem to be my friend this time :(

ps. This is my first mail server, so go easy on me if I did something silly.

---

### Post by DieEier on 2014-05-28
ps. Running ubuntu server 13.10 upgraded to 14.4

---

