---
title: "postfix as backup mx mail server"
date: 2014-04-09
forum: General Help
---

### Post by Marchello_Lippi on 2014-04-09
Hi all, 


my need is to setup postfix as backup mx mail server. 
I mean, this server should receive mail for particular host when main mail server is down. 


I know that I should set dns record, but what configuration should I set at postfix to perform it?

---

### Post by SeijiSensei on 2014-04-09
Just set it up as you would for the primary, but make sure you don't specify [$mydestination]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination") to point to your domain.  That would tell Postfix to deliver the mail locally.  

Postfix should recognize that it's the secondary MX from the domain's DNS records and queue the mail.  When your primary comes back online, it will despool the queued messages.

---

