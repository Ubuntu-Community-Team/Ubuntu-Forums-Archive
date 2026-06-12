---
title: "How do I send mail from a script?"
date: 2007-09-17
forum: General Help
---

### Post by acascianelli on 2007-09-17
How do I send an email from a script, no matter what I use, mail or sendmail, the email is only sent to the local mailbox.  I can't figure out how to actually have it go out.

---

### Post by becatlibra on 2007-09-17
from the command line issue echo "test"|mail [email]youraddress@domain.com[/email] and let me know what you get.

Not sure what you are trying to mail and if you want it set up as a cron job or what. . .

I have a script that is setup to run every minute that mails me:

```

[root@mercury ~]# cat chkkerio
#!/bin/bash

ps -ef > /root/.tempkeriocheck
A=$(cat /root/.tempkeriocheck | grep -c mailserver)
if [ $A -lt 3 ]; then
logger -p local3.notice "KMS not running. Attemping to restart"
cd /etc/init.d
./keriomailserver start
sleep 10
echo "Kerio Broke but it's fine now" | mail -s "It broke!" benjamincathey@catheycompany.com
fi

```

benjamin

---

### Post by dcstar on 2007-09-18
> **acascianelli said:**
> How do I send an email from a script, no matter what I use, mail or sendmail, the email is only sent to the local mailbox.  I can't figure out how to actually have it go out.

To have it "go out" you need a MTA set up correctly (postfix or sendmail do this), and then something like mailx installed to use with the command line.

---

### Post by acascianelli on 2007-09-18
> **acascianelli said:**
> How do I send an email from a script, no matter what I use, mail or sendmail, the email is only sent to the local mailbox.  I can't figure out how to actually have it go out.

No mail command.

---

### Post by acascianelli on 2007-09-18
> **dcstar said:**
> To have it "go out" you need a MTA set up correctly (postfix or sendmail do this), and then something like mailx installed to use with the command line.

I installed postfix, I think I might not have it configured correctly.

---

### Post by becatlibra on 2007-09-24
did you get this figured out - if you installed postfix there should be a command line utility called mail

no?

are you using the box as it's own smtp server or are you trying to use an ISP's smtp server?

---

