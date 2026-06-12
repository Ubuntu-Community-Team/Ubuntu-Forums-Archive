---
title: "Can I send e-mail from mailx using postfix?"
date: 2007-08-29
forum: General Help
---

### Post by ksuchewie on 2007-08-29
I able to send mail using postfix if I do the following:
telnet mail.yourdomain.com 25
ehlo yourdomain.com
mail from: [email]root@yourdomain.com[/email]
rcpt to: [email]fmaster@yourdomain.com[/email]
data
Subject: My first mail for my domain
Hi,
Are you there?
regards,
Admin
. 
quit 



Can I set mailx to do something similar.

---

