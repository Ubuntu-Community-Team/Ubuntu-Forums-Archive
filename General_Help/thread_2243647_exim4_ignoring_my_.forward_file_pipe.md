---
title: "exim4 ignoring my .forward file pipe"
date: 2014-09-10
forum: General Help
---

### Post by peter.h.m.brooks on 2014-09-10
I'm going round in circles - clearly doing something wrong, but I just can't get exim4 to recognise my pipe in the .forward file.

I've made sure that the .forward file is in my home directory. It has the permissions 755. it is owned by the user whose group it is.

kchcl200@KCHADWK02:~$ ls  -l ~/.forward
-rwxr-xr-x 1 kchcl200 www-data 74 Sep 10 12:19 /home/kchcl200/.forward

I've tested it with the filter test:

#exim4 -bf  .forward
abc
.
Warning: no message headers read
Return-path copied from sender
Sender      = [EMAIL="root@kchclinics.com"]root@kchclinics.com[/EMAIL]
Recipient   = [EMAIL="root@kchclinics.com"]root@kchclinics.com[/EMAIL]
Testing Exim filter file ".forward"


Pipe message to: /usr/bin/php5 /usr/bin/mailread.php
Filtering set up at least one significant delivery or other action.
No other deliveries will occur.
#cat ~/.forward#   Exim filter
pipe "/usr/bin/php5 /usr/bin/mailread.php"
#

Oh, and I checked /etc/shells
cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash

An the user home directory is correct:

kchcl200@KCHADWK02:~$ grep kchcl200 /etc/passwd
www-data:x:33:33:www-data:/home/kchcl200/www:/usr/sbin/nologin
kchcl200:x:1002:1002::/home/kchcl200:/bin/bash
kchcl200@KCHADWK02:~$ pwd
/home/kchcl200
kchcl200@KCHADWK02:~$


However, when I send a message, it ignores this completely and just sends it.

The forwarding php program was running perfectly well on another linux host.

As far as I can, I've got a standard 'smart host' configuration - nothing fancy anywhere.

It's as if I have to set something to say 'please look in the filter file.

The message that I sends happily goes through the system and turns up where I've sent it - instead of going to the pipe.

Any suggestions will be most gratefully received...

---

### Post by SeijiSensei on 2014-09-10
I'm a bit confused here.  A .forward file handles incoming mail to an aliased address.  It sounds like you're talking about outbound mail here.  Unless you are sending the mail to the user with the .forward file, any SMTP mailer like exim will not consult the .forward file on outbound mail.

---

### Post by peter.h.m.brooks on 2014-09-11
> **SeijiSensei said:**
> I'm a bit confused here.  A .forward file handles incoming mail to an aliased address.  It sounds like you're talking about outbound mail here.  Unless you are sending the mail to the user with the .forward file, any SMTP mailer like exim will not consult the .forward file on outbound mail.

No, you're not the one confused! I'm the one confused.

You're absolutely right - that's precisely what I've got wrong. 

I see that, what I need to do is to configure a local address with a .forward and send my messages there...

Thank you very much for your help I'm pleased that I asked.

---

### Post by SeijiSensei on 2014-09-11
From a system administration perspective, I prefer to put everything in /etc/aliases  so I have just one place to look.  The .forward file is a convenience for individual users who want to set up forwarding of their mail.  Just remember to run "sudo newaliases" after changing that file.

---

### Post by peter.h.m.brooks on 2014-09-11
Thank you for that advice - you're quite right.

I'm lucky, though. I've go no other system users, the system is only a wiki server, so all that matters is the e-mail forwarding from the server, there are no other users.

---

