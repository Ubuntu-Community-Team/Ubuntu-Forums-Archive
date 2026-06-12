---
title: "trying to set up a local only mail server (&amp; failing miserably)"
date: 2013-03-08
forum: General Help
---

### Post by lancsDavid on 2013-03-08
ok. 6 days in so far (didn't think it would be nearly this hard)

have a development server.  just want to send emails from drupal/php scripts & have read them in some GUI mail reader

unfortunately, postfix + dovecot(??) + thunderbird = (so far) nothing but headaches

postfix seems to work, but can't figure out how to read emails, where they're going or exactly who is sending them.  nor have i managed to configure thunderbird (i'm not sure where its supposed to pull the emails from)

the attached images are screen grabs of (1) the results of 'mail' in the command line, & (2) the mail log

---

### Post by SeijiSensei on 2013-03-08
When you mean "local only" do you mean no Internet mail, just local accounts? 

Try installing the **mailutils** package, then send a test message from the command prompt like this:

```
echo 'this is a test' | mail -s 'test message' someone
```

replacing "someone" with a valid account on the box.  Does the message get delivered to /var/mail/someone?

Are you trying to connect with Thunderbird on the same machine that runs Postfix and dovecot or from another machine on the network?  If the latter, you'll need to remove the restrictions in both programs that limit them to listening on only the localhost interface.  In dovecot, you need to have a "listen = *" directive.  In Postfix, read this [discussion]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from") of the mynetworks directive.

---

### Post by lancsDavid on 2013-03-12
[ system name: NOLi, mailutils & postfix both installed.  postfix installed with 'local only' option ]

first, major thanks.  what a useful command that is you said.  i've used it to figure out what's going on (as i explain below)

regarding "Are you trying to connect with Thunderbird on the same machine that runs  Postfix and dovecot or from another machine on the network?" - the answer is **the same machine**.

so now, i've got to install thunderbird & dovecot -- is this correct?  will this mean the mail will need to be delivered somewhere else or does it carry on being delivered to the **[FONT=courier new]/var/mail[/FONT]** folder?  & if so, do i have to setup up Thunderbird & Dovecot to somehow access it from this folder or what?


[HR][/HR]HOW MY MAIL SETUP CURRENTLY SEEMS TO BE WORKING (with just Postfix & Mailutils)

have seen that mail sent with it gets delivered to [FONT=courier new]**/var/mail**[/FONT] & [FONT=courier new]**/var/spool/mail**[/FONT] (they seem to be clones of each other??)

in my [FONT=courier new]**/etc/aliases**[/FONT] file i've got
[FONT=courier new][B]postmaster:    root
admin:        root
david:        root[/B][/FONT]

so perhaps understandably all mail sent to postmaster, admin & david gets delivered to the root file in [FONT=courier new]**/var/mail**[/FONT]  ('root' is a simple text file i'm presuming).  also, mail sent to brian@NOLi (a non-existent account) also gets delivered here, together with a MAILER-DAEMON 'Undelivered mail returned to sender' system email

plus, by adding ', localhost.com' to the [FONT=courier new]**/etc/postfix/main.cf**[/FONT] file, now mail sent to [EMAIL="david@localhost.com"]david@localhost.com[/EMAIL], postmaster@localhost, etc also get delivered properly

in [FONT=courier new]**/var/mail**[/FONT] (or [FONT=courier new]**/var/spool/mail**[/FONT] ) i've got 2 other files 'fmaster' & 'www-data'.   fmaster i understand.  its another user i added using the 'useradd' command - & any mail sent to it with the command goes to this file.  www-data i'm not sure about as yet

[HR][/HR]

---

### Post by SeijiSensei on 2013-03-13
The www-data "user" is the one that Apache runs as.

If you are running dovecot, then you can set up Thunderbird to use IMAP.  I suspect it's possible to tell TBird simply to connect to a local file, but I've never done that.  I'm usually interested in connecting to the server from multiple locations and multiple accounts, so I need an IMAP server.

If you don't care about a GUI, you could install **alpine** and configure it to use /var/mail/username directly.  The default "mbox" format is simply a single file that contains all the messages with an extra carriage return to delimit the end of each message.

---

