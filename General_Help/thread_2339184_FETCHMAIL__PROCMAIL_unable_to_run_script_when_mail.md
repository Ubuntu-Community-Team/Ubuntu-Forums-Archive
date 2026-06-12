---
title: "FETCHMAIL / PROCMAIL: unable to run script when mail is received"
date: 2016-10-05
forum: General Help
---

### Post by megamania on 2016-10-05
Hi,
I'm trying to set up Fetchmail and Procmail for a single task: run a script when a specific email is received. When an email from "self@gmail.com" with subject "TEST" is received, I need procmail to run a script and do nothing else.

With my current configuration, Fetchmail collects the emails and forwards them to Procmail. However, for every new email received, I get the following message and the script is not executed:

> reading message [email]user@gmail.com@gmail-imap.l.google.com[/email]:9 of 9 (2904 header octets) (216 body octets) not flushed

If no new messages are found, procmail exits without warnings.

These are my configuration files:

fetchmailrc:
```
poll imap.gmail.com protocol IMAP 
   user "user@gmail.com" is gian here
   password 'mypassword'
#   fetchlimit 1
   keep
   ssl

mda "/usr/bin/procmail -f %F -d %T";
```

procmailrc:
```
# .procmailrc
PATH=/usr/bin:/usr/local/bin
MAILDIR=$HOME/.mailspool   # all mailboxes are in .mailspool/
DEFAULT=$HOME/.mailspool/gian
LOGFILE=/dev/null
SHELL=/bin/sh


:0
* ^From:self@gmail.com
* ^Subject:TEST
| sh /home/gian/test.sh
```

What am I doing wrong?

---

### Post by SeijiSensei on 2016-10-06
I don't use Maildir, but shouldn't the spool be someplace outside the $HOME tree?  On a standard system using mbox, mail is spooled in /var/mail or /var/spool/mail with individual files representing each user.  Is $HOME/.mailspool the standard for Maildir setups, or should it be somewhere outside /home?

Also don't set LOGFILE to /dev/null until you're sure everything is set up correctly.  Have the log written to a file in $HOME.  I'd also include "VERBOSE=yes" in the options at the top.

Now let's look at the recipe.  Neither of those tests will match the From or Subject fields because they include one or more spaces between the colon and the rest of the entry.  You need to use regular expressions like these:

```

:0
* ^From:**.***self@gmail.com
* ^Subject:**.***TEST
| sh /home/gian/test.sh

```

Have you read "[man procmailrc]("https://linux.die.net/man/5/procmailrc")" and "[man procmailex]("https://linux.die.net/man/5/procmailex")"?

I've never run fetchmail on a machine with no MTA like sendmail or Postfix.  I use CentOS on servers where procmail is invoked by the MTA.  In those cases fetchmail will hand the mail to the MTA for further processing and delivery.

---

### Post by megamania on 2016-10-06
> **SeijiSensei said:**
> You need to use regular expressions like these:

Following your suggestions, I finally managed to get it to work. Actually, I just had to change the recipe using the regular expression that you provided. I thought it wasn't needed because I was looking for an exact match (my ignorance).

As a side note, I also had to remove "sh" before the script name:
```

:0
* ^From:**.***self@gmail.com
* ^Subject:**.***TEST
| /home/gian/test.sh

```


THANK YOU for your help!

---

