---
title: "Help needed setting up SSMTP"
date: 2013-08-05
forum: General Help
---

### Post by bill-lancaster on 2013-08-05
I wish to send emails from the command line using SSMTP.
I would like the messages to appear From: [email]bill-lancaster@lineone.net[/email]
Have fiddled around with /etc/ssmtp/ssmtp.conf but really don't know what I'm doing.

Can anyone help?

Kubuntu 12.10

---

### Post by bill-lancaster on 2013-08-05
Gmail seems to used in most examples using ssmtp so I thought I'd try that for a start.

ssmtp.conf was set as follows:-

root=wlancaster44@gmail.com
mailhub=smtp.gmail.com:587
AuthUser=wlancaster44@gmail.com
AuthPass=xxxxxxx
FromLineOverride=NO
UseSTARTTLS=YES

Then command line:-


:~$ ssmtp To: [email]fred@someisp.co.uk[/email]
From: [email]wlancaster44@gmail.com[/email]
Subject: test
Hello!
control+D

The email arrives at "fred@someisp.co.uk" OK but gmail has a problem.

Mail Delivery Subsystem <mailer-daemon@googlemail.com>
12:07 (7 minutes ago)

to me 
Delivery to the following recipient failed permanently:

     To:@wlancaster44@gmail.com

Obviously I need help!

---

### Post by slickymaster on 2013-08-05
> **bill-lancaster said:**
> Gmail seems to used in most examples using ssmtp so I thought I'd try that for a start.

ssmtp.conf was set as follows:-

root=wlancaster44@gmail.com
mailhub=smtp.gmail.com:587
AuthUser=wlancaster44@gmail.com
AuthPass=xxxxxxx
FromLineOverride=NO
UseSTARTTLS=YES

...

In your ssmtp config file, add the following line between the mailhub and AuthUser parameters```
 rewriteDomain=gmail.com 
``` so it reads like this```
root=wlancaster44@gmail.com
mailhub=smtp.gmail.com:587
rewriteDomain=gmail.com
AuthUser=wlancaster44@gmail.com
AuthPass=xxxxxxx
FromLineOverride=NO
UseSTARTTLS=YES
```

Also, see this: [Send Gmail from the Linux Command Line]("http://tuxtweaks.com/2012/10/send-gmail-from-the-linux-command-line/")

---

### Post by bill-lancaster on 2013-08-05
Thanks stickymaster,

Your sugestion produces:-

Delivery to the following recipient failed permanently:

     To:@gmail.com

Again, mail arrived at destination OK

Also, the settings proposed in the link you sent produce the same result.

---

### Post by bill-lancaster on 2013-08-05
tried using mail instead of ssmtp:-


:~$ mail  [email]bill@gwldevelopments.co.uk[/email]

mail arrives OK and no message left at gmail

So this will suit my needs but now I need to find out how tp have the email's From: to show as [email]bill-lancaster@lineone.com[/email]

---

### Post by slickymaster on 2013-08-05
> **bill-lancaster said:**
> tried using mail instead of ssmtp:-


:~$ mail  [EMAIL="bill@gwldevelopments.co.uk"]bill@gwldevelopments.co.uk[/EMAIL]

mail arrives OK and no message left at gmail

So this will suit my needs but now I need to find out how tp have the email's From: to show as [EMAIL="bill-lancaster@lineone.com"]bill-lancaster@lineone.com[/EMAIL]


To send mails from command-line the mail command alone isn't enough. You also need a properly configured mail transfer agent (MTA) and personally I'd recommend you to use [mailsend]("https://code.google.com/p/mailsend/").

There are lots of online sources on how to configure MTAs:
[http://wiki.debian.org/sSMTP](http://wiki.debian.org/sSMTP)
[https://wiki.archlinux.org/index.php/SSMTP](https://wiki.archlinux.org/index.php/SSMTP)
[http://msmtp.sourceforge.net/documentation.html](http://msmtp.sourceforge.net/documentation.html)
[http://www.untroubled.org/nullmailer/HOWTO](http://www.untroubled.org/nullmailer/HOWTO)
[http://esmtp.sourceforge.net/doc.html](http://esmtp.sourceforge.net/doc.html)

---

### Post by bill-lancaster on 2013-08-05
Thanks again,

Through you help I found [http://ubuntuforums.org/showthread.php?t=1127478](http://ubuntuforums.org/showthread.php?t=1127478) wich worked first time

Bill

---

