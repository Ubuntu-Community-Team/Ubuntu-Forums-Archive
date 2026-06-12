---
title: "connect from unknown"
date: 2013-10-23
forum: General Help
---

### Post by bibble235 on 2013-10-23
Hi Folks,

Getting a lot of mail which is from an unknown host. I.E. postfix produces

 grep "connect from unknown" /var/log/mail.log

 postfix/smtpd[21643]: connect from unknown[181.65.10.237]
 postfix/smtpd[23319]: connect from unknown[190.166.211.209]

I understand I can add 

 reject_invalid_hostname

to postfix but I would like to first see what e-mail I may be losing before I do this. What I would like is to redirect the e-mail when this occurs to a different user account. See whether the change makes sense and then add it to postfix.

My environment is 
 Ubuntu Server 12.10
 Dovecote
 Postfix

Thanks

---

