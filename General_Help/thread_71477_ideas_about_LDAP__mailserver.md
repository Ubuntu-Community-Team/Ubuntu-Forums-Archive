---
title: "ideas about LDAP / mailserver"
date: 2005-10-03
forum: General Help
---

### Post by ShagzModo on 2005-10-03
Hi all...
Has anyone experience setting up a mailserver with LDAP user database?
What are good servers?
I am currently exploring options on fasing out microsoft active directory and exchange, the total environment will be max. 50 users. any tips and advice is welcome.

kind regards,

Schagzmodo

---

### Post by Tinwood on 2005-10-06
[quote=ShagzModo]Hi all...
Has anyone experience setting up a mailserver with LDAP user database?
What are good servers?
I am currently exploring options on fasing out microsoft active directory and exchange, the total environment will be max. 50 users. any tips and advice is welcome.

kind regards,

Schagzmodo[/quote] 
Hi

I use Courier-IMAP and Postfix as a mail server. Both co-operate with OpenLDAP which would provide your integration with Windows. You're also going to need Samba (installed by default).

Unfortunately, Exchange IS an excellent mail server with Outlook and I'm not sure if anything can quite replace it yet although there are some good things coming along. LJ did an article on groupware recently: [http://www.linuxjournal.com/article/8214]("http://www.linuxjournal.com/article/8214")

HTH
-- 
Alex.

---

