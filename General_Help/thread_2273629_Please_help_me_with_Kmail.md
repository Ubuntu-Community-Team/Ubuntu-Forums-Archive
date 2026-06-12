---
title: "Please help me with Kmail"
date: 2015-04-14
forum: General Help
---

### Post by uvanov on 2015-04-14
Hi, people!

I'm using kubuntu 14.04 and the Kmail is not working, it sends e-mails, but doesn't receive nothing. I have two active accounts via imap server.

I REALLY NEED AN E-MAIL CLIENT, and preferably some that could be run by an user without PhD in software engineering. Please recommend me what should I install, I'm really very disappointed by Kmail, I need something that just works, please recommend me something.

In the software center I can't see nothing else except Kmail, where should I look?

Thank you in advance.

---

### Post by Scunizi on 2015-04-14
It sends email but doesn't receive email tells me that you haven't configured it correctly.  Some online email providers (ie Gmail and others) require that you turn on imap services in the settings of your account. You may also have the wrong port listed in kmail for the service you are using.  Any other email program may have this issue with configuration.  They all "just work" when setup correctly.  This is true on Windows boxes too. Check this link for suggestions on email clients [http://blog.mailcloud.com/technology/linux-email-client-seriously/](http://blog.mailcloud.com/technology/linux-email-client-seriously/)

---

### Post by uvanov on 2015-04-14
Linux is very fun when I learn and use it for my personal intellectual development, but it's quite a challenge, when a man really needs something EASY and USABLE for work, not for fun. Anyway, now I've just accessed my e-mail via Squirrelmail on the web and now I have the whole time of the Universe to learn how to set up my e-mail, if we assume it's possible to be set by a common user, who's not a linux guru.

Thank you very much for your cooperation and wish you all the best!

---

### Post by Scunizi on 2015-04-14
No problem.  Remember, setting up an email client is the same on Window, Mac or Linux.. the email client needs certain information for it to connect and work correctly.  My main computer has been an Ubuntu box for the last 7 years.  It just gets better and better. Although I have switched to Kubuntu because I like the KDE environment better than Unity.

---

### Post by SeijiSensei on 2015-04-15
For an alternative to KMail, try Thunderbird.  It's in the repositories: "sudo apt-get install thunderbird".

---

### Post by buzzingrobot on 2015-04-15
> **uvanov said:**
> Hi, people!

I'm using kubuntu 14.04 and the Kmail is not working, it sends e-mails, but doesn't receive nothing. I have two active accounts via imap server.



Email is sent via your SMTP account. Since you say that's working, you have configured it correctly.

Mail is received via your IMAP accounts. Check *all* of KMail's settings to be sure you have configured them correctly:  Server name, port number, username, password, etc. (If your username is not the same as your email address you will need to change that manually). 

KMail does display a configuration "wizard" on first use which will attempt to automagically set up an account if it finds the email address and username listed online, as do many other mail apps.  They are fallible.

---

