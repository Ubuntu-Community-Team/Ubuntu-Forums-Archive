---
title: "email notifications for logins on my pc"
date: 2019-12-06
forum: General Help
---

### Post by pandaeyes on 2019-12-06
so i have a fresh install ( ubuntu 19.10) on my laptop which is used mostly for casual use and im looking for a way to make ubuntu notify me via email whenever someone logins to my pc (mostly via keyboard )
how can i do this? maybe though some kind of script at startup or somekind of application?
there's only one user

---

### Post by TheFu on 2019-12-06
**logwatch** will email daily reports about a system.  Logins, users, installed packages, removed packages, etc.
You can setup **fail2ban** to monitor any log file and provide notifications as you like.

Both of those tools assume you have a working MTA that can send email where you want.  That is a completely separate issue. There are lots of options and guides, but how to accomplish it depends on whether the system is a full email server and working or if it is a typical residential desktop that must send all email through some ISP-provided email gateway.

---

### Post by pandaeyes on 2019-12-10
so... what would be a easy way to use a gmail account dedicated to this purpose and send email notifications about logins (failed or successful attempts) through my device when it gets connected online?

---

### Post by pandaeyes on 2019-12-29
so i found this [link]("https://linuxaria.com/pills/email-on-shutdown-and-restart-linux") ... looks quite promising. 
if it does work...
-what would i need to modify this in order to work for me?
(i have zero experience in scripting..)
-would i need to set up an email account to send the notifications to another?

---

### Post by TheFu on 2019-12-29
I don't know anything about gmail except that my mail servers sometimes block gmail as a spamming domain for a few hours daily.  That's why I didn't respond previously - it is outside my knowledge.

The link in post #4 above is for the old rc-init system.  That hasn't been used since around 2011.  After that came upstart, then systemd. I think they are backwards compatible, but I honestly don't know.  If I were creating an init setup for this, I'd look up how systemd wants it done.  They claim the systemd method is easier for new people to learn/understand.  Google found this: [https://www.linode.com/docs/quick-answers/linux/start-service-at-boot/](https://www.linode.com/docs/quick-answers/linux/start-service-at-boot/) and there were lots of other results. It is a reputable source, but it might not make sense to you.  That's the most important part.  Looks fairly easy.

As for sending FROM your Linux machine, the account used would normally be the account the daemon/service is running under.  While it is possible to setup email accounts that are completely separate from logins, that isn't normally done on small systems where all the users have either file storage or logins via ssh.  I only do all the separate email account DB stuff for corporate email setups.  Whatever makes the most sense for you.

---

### Post by pandaeyes on 2019-12-29
how hard is to make a script that would run through a cli app to send an email notification at startup?

dont know much about pc but sounds pretty easy for someone who has the experience

im just a newbe trying to make this work :P for my piece of mind

but thank you though
any reply appreciated

---

### Post by TheFu on 2019-12-29
```
$ echo "the main message here" | /usr/bin/mail  -s "Some subject" foo\@gmail.com
```
The main message can alternatively be inside a file.
```
$ /usr/bin/mail   -s "Some subject" foo\@gmail.com < ~/mail-message
```

This assumes an MTA is setup and working correctly.  The MTA is normally postfix, sendmail, qmail, exim, ... something like that./usr/bin/mail

I send a daily message to an old friend this way using a crontab entry.

---

### Post by pandaeyes on 2019-12-29
mta is setup with mailutils, tested and worked successfully (first time for me)
so how would i proceed for the script?

---

### Post by pandaeyes on 2019-12-30
maybe adding a simple command through statup applications could do the trick?

---

### Post by pandaeyes on 2019-12-31
did it
it was quite simple
but if you dont have the knowledge it might take a while...

---

### Post by TheFu on 2019-12-31
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) will provide the beginning level knowledge, in the correct order, for the most efficient learning.

---

