---
title: "Ubuntu Webserver"
date: 2012-10-20
forum: General Help
---

### Post by AvengerX9 on 2012-10-20
Hi,

I think I got a problem with sending emails from my Ubuntu webserver. The web application I'm using to send emails does not report any errors, but I never receives the email. So what can I do to figure out whats wrong.

Here is the error logs that I just received

> 
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found


I guess I need to install something ? :) Help is appreciated. Thanks

---

### Post by AvengerX9 on 2012-10-20
I tried this, but it seems to load a lot when I try to send from the web interface and it still won't send any mails

$ sudo apt-get install sendmail
$ sudo sendmailconfig

---

### Post by Lars Noodén on 2012-10-20
You might look at Exim or Postfix instead, the configuration is much, much simpler than Sendmail's.  Also you might have to send outgoing mail via another MTA, say Google's or that of your ISP or something else.

---

### Post by AvengerX9 on 2012-10-20
Okay, I will install postfix instead

---

### Post by AvengerX9 on 2012-10-20
How can I configure the Postfix. I get a dialog box with some options but it dont respond to the mouse click or any keys ?

---

### Post by AvengerX9 on 2012-10-20
seems like sendmail is already installed on the Webmin interface. So why won't my site send any mails ? and what does the error means ?

---

### Post by Lars Noodén on 2012-10-20
> **AvengerX9 said:**
> How can I configure the Postfix. I get a dialog box with some options but it dont respond to the mouse click or any keys ?

If that's during the installation, you'll need to go to then next screen by pressing OK.  Then you'll have the choice of using a smart host or setting up a satellite system.  You do have another mail server you can use as a smart host?  Or do you have your own static IP address with a registered hostname in DNS?

---

### Post by AvengerX9 on 2012-10-20
Im clicking OK but nothing happens :)

---

### Post by AvengerX9 on 2012-10-20
but going from Sendmail to Exim or Postfix. Would that require me to alter the php code ?

---

### Post by AvengerX9 on 2012-10-20
I will try install it again from webmin

---

### Post by Lars Noodén on 2012-10-20
If you are installing via the shell, the mouse won't work.  You'll need to use tab to move between choices and return to select your choice.

---

### Post by AvengerX9 on 2012-10-20
Hmm, its allready installed now. Probably not setup correctly though :) How can I check if it works or not ?


Edit: I got a static IP address and a domain name. Name.com is where I manage the DNS stuff

---

### Post by Lars Noodén on 2012-10-20
> **AvengerX9 said:**
> Hmm, its allready installed now. Probably not setup correctly though :) How can I check if it works or not ?


Edit: I got a static IP address and a domain name. Name.com is where I manage the DNS stuff

When it is all set up you should be able to send mail.

```

echo Test | mail -s "this is a test" AvengerX9@example.org

```

A static IP and hostname will help.  I recommend posting over in the Server subforum with a more descriptive heading.  This is about postfix, exim or sendmail and not yet about a web server. ;)

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

---

