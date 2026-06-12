---
title: "Ubuntu 7.10 Postfix Question/Problem"
date: 2008-04-14
forum: General Help
---

### Post by nosco on 2008-04-14
Hello, Just have a few questions.

I have a working Ubuntu 7.10 LAMP server with Postfix/Citadel-Dovecot-BIND9-Webmin-Roundcube installed.

Everything seems to be working properly with Postfix except creating users to access email. I tried creating users with webmin but I cannot login to email via roundcube or thunderbird etc.. I get an imap auth failure when i check roundcube logs.

I also tried using useradd and adduser from the terminal but I cannot login with roundcube or thunderbird. The only user I can login with is the one i created when following a guide to setup postfix ( I believe it was useradd -f -m username).

I was searching around for an answer to my problem but I never found a resolution.

Basically  I want to be able to host several virtual domains (Which I already have working great with Apache2) and each domain have their own e-mail addresses @domain.com. 

I came across a post regarding Citadel Server, so I installed it and it works really good. But I don't think it's what I'm looking for. I have not found a way to have several domains with their own [email]user@domain.com[/email] with Citadel.

Is there a way I can have multiple domains with their own database/calendar shares etc with Citadel? or should I stick to Postfix and use roundcube for an IMAP webclient.

Sorry If my post is hard to follow, thanks in advance.

---

### Post by jameslyden on 2008-04-23
Reading through the Citadel documentation online didn't provide any hints about how the multiple domain support is configured, but there's always an inelegant solution: copy the install to a different directory for every domain, and configure them independently (or better yet, have the person who wants you to host the domain configure it). As far as virtual mailboxes goes, there's a fairly tried-and-true method using postfix/mysql out there. A couple link for that setup:

[http://howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

---

