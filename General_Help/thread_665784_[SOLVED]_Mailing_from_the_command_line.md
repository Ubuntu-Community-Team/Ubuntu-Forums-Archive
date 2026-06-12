---
title: "[SOLVED] Mailing from the command line"
date: 2008-01-12
forum: General Help
---

### Post by ksadil on 2008-01-12
I would like to be able to send an email from the command line to remote email addresses. I have mailutils and citadel installed for my domain. I cannot seem to find where to specify that the "mail" command should use the smtp server on 127.0.0.1.

When I try "mail <my@email.address> -s ......." my ISP responds with an email saying "You must log in to send mail from <mydomain.com>. Using a gui client I am able to send mail through my citadel server without any problems.

Any ideas?

Thanks,
Kim

---

### Post by ksadil on 2008-01-12
citmail is the comand line substitute for sendmail, so rename the old sendmail command to sendmail.old and ln -s the citadel command to where sendmail used to be.

---

