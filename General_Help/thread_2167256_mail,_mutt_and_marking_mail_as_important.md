---
title: "mail, mutt and marking mail as important"
date: 2013-08-13
forum: General Help
---

### Post by zealibib slaughter on 2013-08-13
Hello everyone,  I hope someone has a solution for this.  I have a shell script which i run as a cron job every day that greps auth.log for failures on ssh it then uses mail to send any failures to my system mailbox at /var/mail.  I use mutt to read my mail.  What I would like is some way of automatically flagging these messages as important based on the subject. I have read the man pages for both mail and mutt and googled for hours trying to find a way but still haven't. Does anyone have a solution?

edit: before anyone asks why i don't just cat the log file and grep for any lines that matches what I am looking for this is on a headless server I ssh to and when I login it will tell me if I have messages waiting.  I can't rely on just that because I have scripts monitoring other things which sends mail too.

---

### Post by zealibib slaughter on 2013-08-19
Anyone?

---

### Post by RichardET on 2013-08-19
i used to use the pine mailer from univ. of washington;  it is easily compiled from source from their web site and is a great text based mailer with a menu.

---

