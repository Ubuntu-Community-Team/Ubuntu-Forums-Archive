---
title: "Courier IMAP Question with Postfix"
date: 2007-11-15
forum: General Help
---

### Post by atjensen11 on 2007-11-15
Hello,

I followed the tutorial posted by Flurdy on setting up an email server with several whistles and bells.  After some typos of my own (and one or two on Flurdy's part) it appears that I have a fully functioning system.

FYI - The tutorial I followed is at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

My problem is that I cannot view emails with an email program through an IMAP account or Squirrelmail.  It is like Courier is looking at the wrong location for emails.

I have Webmin installed and can view the emails in the /var/mail/virtual/[user] folder.  There are emails in this location.

Postfix is delivering the messages to this location.  I can also send emails externally.

I can telnet into localhost through Putty to both ports 25 and 143 with no problems.  I can login to IMAP with the telnet connection on 143, but it also shows no new messages.

What am I doing wrong here?

Thanks,
Tom

Ubuntu 7.10 Server Edition
Dell GX260
Postfix, Courier, ClamAV, Spamassassin, Squirrelmail all using MySQL backend

---

### Post by PeterWhittaker on 2007-11-19
According to the Courier home page, Courier expects mail to be in the user's home directory, not /var/spool or anywhere else. Refer to the section "upgrade path" on the page

[INDENT][http://www.courier-mta.org/intro.html](http://www.courier-mta.org/intro.html)[/INDENT]

from which I quote:

[INDENT]Courier expects system mailboxes to be in the users' home directories. If your system mailboxes are all stored separately, in /var/spool/mail or somewhere else, you'll need to use a local delivery agent such as procmail.[/INDENT]

Can't help you with procmail, though.

Good luck,

pww

---

### Post by atjensen11 on 2007-11-19
I have read that statement before as well and am not sure that it applies in this situation.  I don't know that for a fact, but there is also this line that states:

> Courier's IMAP server, webmail server, and mail filter are available as independent packages that can be used with other mail servers (as long as the other mail servers store mail in maildirs).

I am using Postfix as my MTA and I am using maildirs.  I am trying to allow webmail via Squirrelmail or IMAP access via Courier-IMAP for virtual users.  So I really don't know if I need (or want) each virtual user to have a HOME directory.

Any input is welcome.

Thanks,
Tom

---

### Post by atjensen11 on 2007-11-20
I think I solved my problem.  It may have been any one of the two items below.  I noticed today that Dovecot was installed and set to start up by default in Ubuntu.  I had installed and intended on using Courier.  So I disabled Dovecot from running at startup.  I then rebooted the machine just to be sure.  That is when I noticed the following lines in my mail log.

> Nov 20 10:26:15 gopher authdaemond: Installing libauthmysql
Nov 20 10:26:16 gopher authdaemond: Installation complete: authmysql
I don't know that this had any impact or not, but now everything appears to be working as I would expect.

Tom

---

