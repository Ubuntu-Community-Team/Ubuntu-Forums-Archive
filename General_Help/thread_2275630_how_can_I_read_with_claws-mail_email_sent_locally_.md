---
title: "how can I read with claws-mail email sent locally to root@localhost???"
date: 2015-04-27
forum: General Help
---

### Post by a-you on 2015-04-27
I use claws-mail in ubuntu studio 14.4 trusty, which uses the xfce desktop. I have configured postfix so that email sent on this machine locally by programs like for example rkhunter to [EMAIL="root@localhost.locald"]root@localhost.locald[/EMAIL]omain end up in an mbox called /var/mail/myusername. That's all good :-). But I'm trying to access/import/somehow read that mbox in claws-mail and it's not working.

I have tried creating a new account in claws, choosing "Local mbox file" as the account type but when I click "Auto-configure" it returns "Failed." I did create a folder into which the email should go from within claws' "Edit accounts" dialog too and I went through the settings and selected everything that seemed appropriate (though I'm not an expert), turning off SSL for example. By the way I also chose "Use mail command rather than SMTP server" in that dialog just because I don't want to send email, only to read it in claws. In that dialog under "Mail address" I entered [EMAIL="myusername@localhost.locald"]myusername@localhost.locald[/EMAIL]omain.

If anybody knows how to do this and can explain I'd appreciate it! Thanks!! Interwebs searches turned up only one answer so far but it was way too brief and so I'm still stuck.

I added myself to the "mail" group by the way too.


Edit: huh, now it seems to be spontaneously working. Maybe because I restarted the computer(???)

In case it might help somebody to know, the above mentioned settings are what seem to have worked after all:
"Local mbox file" as the account type in claws' Configuration->Edit accounts and in that dialog entering (or leave it as this if it already sets it that way by default) "/var/mail" (without quotes) for "Local mailbox." In "Mail address" put [EMAIL="yourusername@localhost.locald"]yourusername@localhost.locald[/EMAIL]omain.

This is I believe assuming that you have configured postfix (if that's what you're using) to deliver such email from applications to your /var/mail folder. What worked for me was this:
[http://ubuntuforums.org/showthread.php?t=2274702](http://ubuntuforums.org/showthread.php?t=2274702)

---

### Post by vitaly7 on 2016-01-09
thank you
iam using Debian 8 amd64 Jessie / Xfce4 /ClawsMail3.11
post was quickly useful when try to figure it out with the same problem...
additionally able to put some value on that, if do not have any configured smtp server or posix to send messages through smtp, can check **"Use mail command rather then SMTP server" **on the same account configuration screen, andleft** "/usr/sbin/sendmail -t -i**" here in that field...
works without any issues to send messages locally

---

