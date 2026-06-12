---
title: "Sendmail to external smtp server?"
date: 2004-12-11
forum: General Help
---

### Post by charleyramm on 2004-12-11
I am writing a cgi perl script to send emails from a web form. I want to run it on my local computer, but i want to send the mail using smpt.myisp.com. Ill  print the script to try and give you some idea if what i want to do.  I was hoping there is some way to tell 'MAIL' or sendmail or whatever to use my isp's smtp server.  Is there a config file or something i could use?


```

open (MAIL, "|/usr/sbin/sendmail -t -oi") or
	die "Can't fork for sendmail: $!\n";

print MAIL "From: charleyramm\@hotmail.com\n";
print MAIL "To:", $form{email}, "\n";
print MAIL "Subject: Email form: chuck54.com\n\n";

print MAIL "$form{comments}\n";
close(MAIL);

```

---

### Post by tomchuk on 2004-12-11
Are you on a stock Ubuntu system? Have you screwed around with different MTA's? If not you should have postfix installed and running, and all you need to do is edit /etc/postfix/main.cf and add your ISP's smtp server as the **relayhost** parameter. /etc/init.d/postfix restart will restart postfix, using the new relayhost.

---

### Post by tomchuk on 2004-12-11
Are you on a stock Ubuntu system? Have you screwed around with different MTA's? If not you should have postfix installed and running, and all you need to do is edit /etc/postfix/main.cf and add your ISP's smtp server as the **relayhost** parameter. /etc/init.d/postfix restart will restart postfix, using the new relayhost.

Oh, just re-read your script - you may have some problems with the mail originating at your IP and being sent to Hotmail - they will bounce anything sent from a dynamic IP range. You'll want to use Net::SMTP to send mail directly though your ISP's server.

---

### Post by charleyramm on 2004-12-11
My smtp server requires a password. Is there some way i can set a username and password for 'relayhost'? 
 /etc/postfix/main.cf found and edited. I will try it without a password and see what it says. 

 This computer is actually running debian testing I think. I've recently converted my laptop to ubuntu, and I love it.

---

### Post by tomchuk on 2004-12-11
Here's a good link, read the part about smtp-auth: [http://www.hserus.net/postfix.html](http://www.hserus.net/postfix.html)

---

### Post by charleyramm on 2004-12-11
Ok i think im getting close now. Added a couple of 'sasl_foo' lines to main.cf and a separate password file. But still not working.

 Does someone know what this might mean?
```
bitch:/home/charley# perl mail.pl
postdrop: warning: unable to look up public/pickup: No such file or directory

```

This is mail.pl (i wrote this so it could be VERY wrong :roll:  ) 
```
#!/usr/bin/perl
open (MAIL, "|/usr/sbin/sendmail -t -oi") or
        die "Can't fork for sendmail: $!\n";
print MAIL 'From:charleyramm@fatsmail.fm\n';
print MAIL 'To:charleykjramm@fastmail.fm\n';
print MAIL "Subject: Email form: chuck54.com\n\n";

print MAIL 'The content of my email';

close(MAIL);

```

---

### Post by tomchuk on 2004-12-12
Might be a permissions problem, try:

```

sh /etc/postfix/post-install set-permissions 

```

---

