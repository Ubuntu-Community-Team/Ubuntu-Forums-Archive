---
title: "command line email"
date: 2007-03-27
forum: General Help
---

### Post by gatoruss on 2007-03-27
I am try to configure xboard to play email chess. The documentation says that I need to set a path for the email configuration for the email program that I want to use to email moves. Specifically, the documentation states :

> 
-mailprog <mail program>
The program used by cmail to send email messages. This defaults to the
environment variable `$CMAIL_MAILPROG' or failing that
`/usr/ucb/Mail', `/usr/ucb/mail' or `Mail'. You will need
to set this variable if none of the above paths fit your system.


I use evolution. Can anyone suggest how I could configure evolution to work with xboard and evolution?

Thanks.

gatoruss

---

### Post by Mr. C. on 2007-03-27
Your cmail program wants to talk with a command line mailer, like mailx, and receive its email locally as well.  You will need to configure your system with mailx, which also comes with postfix, or use another SMTP mailer, or procmail.

Section 10.3 [http://tim-mann.org/xboard/xboard_10.html](http://tim-mann.org/xboard/xboard_10.html)  describes how you have to send the contents of the email to the cmail command for parsing.

So, you need to be able to place your cmail messages into a file for processing (which you can do with procmail, and Evolution) and be able to send the messages via command line SMTP mail.

Since Evolution places your mail into Maildir folders, you could either create a rule to move your cmail messages into a folder (eg cmail-incoming) and the process either manually or by procmail automatically.

Does this help?
MrC

---

