---
title: "Backup w/ notification?"
date: 2012-10-15
forum: General Help
---

### Post by bertmanphx on 2012-10-15
Hello all,
I have a machine that is a simple file server in an office, running 12.04.
The default backup Deja Dup will work just fine for the task of backing up software.  However, I'd really like an email notification sent when it's complete.

Is there something else that could perform this simple task of backup AND an email that it either was successful, or failed?

Thank you,

bertmanphx

---

### Post by ALinuxWindowsBalance on 2012-10-15
> **bertmanphx said:**
> Hello all,
I have a machine that is a simple file server in an office, running 12.04.
The default backup Deja Dup will work just fine for the task of backing up software.  However, I'd really like an email notification sent when it's complete.

Is there something else that could perform this simple task of backup AND an email that it either was successful, or failed?

Thank you,

bertmanphx

try this list
[http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895](http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895)

---

### Post by cbraxton on 2012-10-15
> **bertmanphx said:**
> 
Is there something else that could perform this simple task of backup AND an email that it either was successful, or failed?

I generally run the backup from a shell script that checks exit status of whatever program is doing the backup (tar, rsync, etc.) and sends an appropriate email notification.

There are a number of ways to to this, a couple of simple command-line mailers I've used are *smtpstoat* ([http://www.drydeadfish.co.uk/smtpstoat](http://www.drydeadfish.co.uk/smtpstoat)) and *sendEmail* ([http://caspian.dotconf.net/menu/Software/SendEmail](http://caspian.dotconf.net/menu/Software/SendEmail)).

---

