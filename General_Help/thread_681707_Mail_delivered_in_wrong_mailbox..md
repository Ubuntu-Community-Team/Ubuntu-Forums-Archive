---
title: "Mail delivered in wrong mailbox."
date: 2008-01-29
forum: General Help
---

### Post by mikenuun on 2008-01-29
First of all,
Im new to the forums,
So hi anyway ^^

But the reason i came is that im having a weird problem,
Maybe the solution is close, but for me its a weird problem.

I'm Using Postfix to receive mail and to send mail,
And for the right delivery im using procmail,
But hey, procmail does not place it into the right mailbox !

Sending maile is ok,
So the postfix confgiruration is ok for now
Its just that the procmail doenst place the mail in the users mailbox,

Heres my .procmailrc

# .procmailrc
# routes incoming mail to appropriate mailboxes
PATH=/usr/bin:/usr/local/bin
MAILDIR=/var/mail/$USER
DEFAULT=/var/mail/gevonden
LOGFILE=/var/log/procmail.log
SHELL=/bin/sh

Mail always cames at /var/mail/gevonden, doenst matter for what user it is.
But if i chance the default to /var/mail/$USER , it wont receive mail at all
I dont know what to do, i just want procmail to deliver the right mail in the mailbox for the user.

Further Information :
OS : Ubuntu 6.06 LTS
Kernel : Sparc64

Thanks in advance,

Mike Van Nunen

---

### Post by andrew.46 on 2008-02-04
Hi,

 I can see a little confusion here:

> **mikenuun said:**
>  [...]
I'm Using Postfix to receive mail and to send mail,
And for the right delivery im using procmail,
But hey, procmail does not place it into the right mailbox !
[...]
# .procmailrc
# routes incoming mail to appropriate mailboxes
PATH=/usr/bin:/usr/local/bin
MAILDIR=/var/mail/$USER
DEFAULT=/var/mail/gevonden
LOGFILE=/var/log/procmail.log
SHELL=/bin/sh


The variable Maildir is intended to be the place where procmail *recipes* deliver mail, but I note that you appear to have no recipes? The Default variable is the place where all *other* mail, not affected by procmail recipes is delivered, it does not have to be specified if the system MAIL variable is set elsewhere: perhaps by ~/.bashrc? Try disabling the DEFAULT value in your procmailrc, log out and then type

```
$ echo $MAIL
```

Can I suggest something like the following:

```
# Path
PATH=/usr/bin:/usr/local/bin
# Where procmail recipes deliver:
MAILDIR=/home/$USER/mail
Where all mail is delivered:
DEFAULT=/var/spool/mail/$USER
```

And of course whatever procmail recipes you wish to use to deliver to MAILDIR. Is this any help? I will admit that my use of procmail is limited to a *single user* computer and I have absolutely zero experience with postfix. My own setup is Gmail ==> Fetchmail ==> Procmail ==> mutt  ==> msmtp ==> Gmail.

   Andrew

---

