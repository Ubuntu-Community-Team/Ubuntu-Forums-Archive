---
title: "[SOLVED] Why Will Cron Not Send Me Mail?"
date: 2008-03-28
forum: General Help
---

### Post by cmnorton on 2008-03-28
I have looked at the other posts that popped up when I typed in this title, and I have a question that's a bit of a wrinkle from other similar questions.

On my new workstation, I did not have mailx installed, but I could send mail from the command line using the "mail" command. I installed mailx, and cron's ability to send mail started working. sendmail was installed and running.

My question is this. Which package installed would allow me to send mail from the command line but not from cron?

---

### Post by davidpbrown on 2008-03-28
?Maybe instead just stop the cron sending mail by adding
 > /dev/null 2>&1 
to the end of commands
or just
 > /dev/null
to report only errors.

---

### Post by justleen on 2008-03-28
pff... good question..
Sendmail is normally for sending mail to the outside (or for a mailserver).
mail can is just a tool.. but you need something to handle the mail from Mail.
cron should work without sendmail, for just sending to root/users (localy that is..)
perhaps postfix was installed?

---

### Post by cmnorton on 2008-03-28
No, postfix is not installed. I posted this as more of a curiosity. I'll just remember to grab mailx next time.

---

