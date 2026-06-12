---
title: "Fetchmail won't start - Feisty x86_64"
date: 2007-07-10
forum: General Help
---

### Post by cjb on 2007-07-10
Hi all,

I have installed the x86-64 server edition and installed fetchmail. I'm trying to configure a general purpose mailserver, probably with fetchmail, exim, procmail, spamassassin and a webmail program. However, I haven't done anythign this complex before, so I'm expecting some issues.

There's a fetchmail user in /etc/passwd, and there's a fetchmail link in /etc/rc2.d/. I took a copy of my old (possibly too old?) fetchmailrc file and put it in as /etc/fetchmailrc. The non-commented parts of this file are:

set logfile "/var/log/fetchmail"
set postmaster "cjb"
set bouncemail
set no spambounce
set properties ""
set daemon 60
poll mymailserver.co.uk with proto POP3 timeout 50
       user 'myuser' there with password 'mypassword' is 'cjb' here

The file is owned by the fetchmail user. If I run /usr/bin/fetchmail, the only message I get back is:

fetchmail: no mailservers have been specified.

Nothing is started up and no other mesasges are given. I can ping the mailserver mentioned in /etc/fetchmailrc. No service is started up after booting.

Where do I need to look next? What have I missed?

thanks for any help,

James

---

### Post by cjb on 2007-07-10
Following on...

I tried to reconfigure fetchmail with dpkg. This didn't work, but it did give me a helpful message about not being able to access /var/log/fetchmail.

I "touch"ed /var/log/fetchmail, then chmodded it to 666. fetchmail now runs, and is visible as a process. It's not accessing my email, but that's a different problem! I also haven't installed X (I'm using the serve edition), so I haven't used fetchmailconf. 

Is just creating /var/log/fetchmail going to cause problems? Do I need to set up log rotation separately? Would fetchmail normally log to a different file under Ubuntu?

thanks,

James

---

