---
title: "Procmail will not work after configuration"
date: 2007-06-12
forum: General Help
---

### Post by fall3flake on 2007-06-12
Hello everyone, I'm a bit of a newbie to ubuntu so bare with me.

I'm running 6.10 and I want to get procmail working so it will deliver all the incoming local mail for me.  Eventually I want to use Anomy Sanitizer with it to remove all incoming attachments and put them in a folder, but I'm getting ahead of myself.

I have postfix installed on my system and that is running just fine.  In the main.cf file I added

mailbox_command = /usr/bin/procmail -f- -a "$USER"

so that it will call procmail for mail processing.  I then created .procmailrc file in the local user directory.

SHELL=/bin/sh
PMDIR=$HOME/Procmail
LOG=$PMDIR/pmlog
LOG="
"
MAILDIR=$HOME/Mailbox
INCLUDERC=$PMDIR/rc.testing

# EOF

In the rc.testing file I have

:0:
* ^Subject:.*test
IN-testing

# EOF

I'm really just following the steps from [http://www.ii.com/internet/robots/procmail/qs/#steps](http://www.ii.com/internet/robots/procmail/qs/#steps)

Now what it is suppose to happen is that any email I send to that mailbox without "test" in the subject will go to my regular mailbox and anything which contains it will go to IN-testing mailbox.

After testing however I receive nothing at all.  No In-testing mailbox has been created, no pmlog has even been created.  I then look in my /var/log/mail.log and saw this

Mail-server postfix/cleanup[5387]: D89F6570208: message-id=<BAY128-F3342CE73F5528976A53E0D9E190@phx.gbl>
Mail-server postfix/qmgr[5380]: D89F6570208: from=<me@hotmail.com>, size=1362, nrcpt=1 (queue active)
Mail-server postfix/local[5388]: D89F6570208: to=<user@mail.server.com>, orig_to=<test@server.com>, relay=local, del\
ay=0.42, delays=0.39/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f- -a "$USER")
Mail-server postfix/qmgr[5380]: D89F6570208: removed

I don't really know for sure what it means, but it seems like postfix has sent the mail to procmail to process and then deletes it, but procmail just didn't do anything with it, or maybe it's not even working at all.

At this point I'm really just stuck as I have tried everything and read a lot of tutorial online about postfix and procmail and they don't seem to do anything special that I haven't done.

Anyone with any kind of ideas and input would be greatly appreciated!  Thanks!!!

---

