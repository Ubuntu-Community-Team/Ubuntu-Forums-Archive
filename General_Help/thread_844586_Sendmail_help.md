---
title: "Sendmail help"
date: 2008-06-29
forum: General Help
---

### Post by ivantis on 2008-06-29
I am trying to install a mail server on my ubuntu machine (version 8.04). I installed postfix and sendmail, postfix seems to work okay, but it will not send mail. I have sendmail, but it had the wrong domain. So i removed /etc/mail. Now, when i uninstalled sendmail, i reinstalled it. But it says it cant find /etc/mail/sendmail.cf (No such file or directory). I know that because i removed it, but it wont recreate it???
Would someone be kind enough to let me scp or ftp the /etc/mail directory from their ubuntu, or tell me a way to get /etc/mail back.
Thanks in advance.

EDIT: I solved it with "sudo apt-get --reinstall install sendmail-base"
then "sudo apt-get install postfix".
Mail now works.

---

