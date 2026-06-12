---
title: "Ubuntu Grouware server Citadel"
date: 2007-05-10
forum: General Help
---

### Post by timgerr on 2007-05-10
I have just build a new ubuntu 7.04 server.  I have installed Citadel Groupware server and am having trouble with adding spamassassin and getting it to work with Citadel.  I cannot figure out how to tell spamassassin what the spam and what the ham is.  Has anyone gotten Citadel working with Ubuntu?

Thanks
-T

---

### Post by scotty64 on 2007-06-12
Yes, I have a citadel installation running under Dapper. Installation was easy and everything works fine. The only hickup I get is that it does not shut down properly. When trying to shut down the computer or just citadel it stop at the "shutting down citadel groupware" and fills the terminal screen with dots over time. The only way to bypass this is to kill the citadel processes manually.
About spamassassin: It has an autolearn feature that tries to distinguish ham and spam automatically. 
I created a procmail recipe to trigger the sa-learn program by forwarding ham and spam to two virtual email addresses "mailspam" and "mailok". This needs to be in the mail transport and we are not using it on citadel, but maybe its possible to create a hook. Another alternative would be an external spam/antivirus mailproxy - that is what I am going to try.

Here is the relevant part of the procmailrc:
"munpack" is used in case the spam/ham has been forwarded as attachment.
$DIR is a directory of your choice.


# [email]mailok@services.mydomain.com[/email] trains bayes filter for ham
:0:
* ^To:.*mailok@services.mydomain.com
{
:0wb
* ^Content-Type: text.*
| sa-learn --ham
:0
* ^Content-Type: multipart.*
| munpack -t -C $DIR && sa-learn --ham $DIR && rm -f $DIR/*
}

# [email]mailspam@services.mydomain.com[/email] trains bayes filter for spam
:0:
* ^To:.*mailspam@services.mydomain.com
{
:0wb
* ^Content-Type: text.*
| sa-learn --spam
:0
* ^Content-Type: multipart.*
| munpack -t -C $DIR && sa-learn --spam $DIR && rm -f $DIR/*
}

---

### Post by scotty64 on 2007-06-14
I found the reason for the hangs when shutting down citadel:
The initscript tests for the socket /var/run/citadel/citadel.socket to close and the demon process does not do this when shutting down. Killing the socket manually works as a dirty workaround. I already filed a bug on the citadel bugzilla.

---

