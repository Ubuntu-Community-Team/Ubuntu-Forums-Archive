---
title: "SSMTP hangs"
date: 2019-06-14
forum: General Help
---

### Post by hakelm on 2019-06-14
Not coming to terms with postfix I uninstalled postfix and switched to ssmtp for sending automated mails from my ubuntu 16.04.
I tested my setup on a Raspberry Pi where it worked without a glitch. 
On my Ubuntu ssmtp hangs when I try to send a mail until I press control-D the program terminates and  the mail is delivered. This doesn't allways work.
/etc/ssmtp/ssmtp.conf on the two systems are very similar


If I do
hakelm@nilx:~$ ssmtp [EMAIL="hakelm@smeden.org"]hakelm@smeden.org[/EMAIL]
abc
.


ssmtp hangs but after pressing ctrl-D the mail is sent and  /var/log/mail.err states:
Jun 14 16:09:01 nilx sSMTP[2348]: 550 5.7.1 Username [EMAIL="hakelm@smeden.org"]hakelm@smeden.org[/EMAIL] and sender [EMAIL="root@smeden.org"]root@smeden.org[/EMAIL] doesnt match
(wherever did it get root from?)


/var/log/mail.log:
Jun 14 16:13:19 nilx sSMTP[4330]: Creating SSL connection to host
Jun 14 16:13:19 nilx sSMTP[4330]: SSL connection using ECDHE_RSA_AES_256_GCM_SHA384
Jun 14 16:13:19 nilx sSMTP[4330]: Sent mail for [EMAIL="hakelm@smeden.org"]hakelm@smeden.org[/EMAIL] (500 5.5.2 Error: bad syntax) uid=1002 username=hakelm outbytes=315


Any tip that helps me to resolve this is appreciated.
H

---

