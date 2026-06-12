---
title: "Sendmail installation"
date: 2015-01-09
forum: General Help
---

### Post by minerbog on 2015-01-09
Hi guys,

I'm having trouble with sendmail at the moment.

I think it is installed as the sendmail command runs and there is a sendmail program in the /usr/sbin folder. But when I run ```
apt-get install sendmail
```it tries to install it.

How do I find out if it's installed or not??

Regards,

Gav.

---

### Post by SeijiSensei on 2015-01-09
Installed or running?

Installed:
```
dpkg -s sendmail | grep Status
```

Running:
```
ps ax | grep sendmail
```

or you can test that it is listening by using
```
telnet localhost 25
```
Sendmail will reply with its banner, something like:
```
220 mail.example.com ESMTP Sendmail 8.13.8/8.13.8; Fri, 9 Jan 2015 09:59:36 -0500
```

---

### Post by oldos2er on 2015-01-09
Moved to General Help.

---

### Post by Holger_Gehrke on 2015-01-09
> **minerbog said:**
> 
I'm having trouble with sendmail at the moment.

I think it is installed as the sendmail command runs and there is a sendmail program in the /usr/sbin folder. But when I run ```
apt-get install sendmail
```it tries to install it.


It's probably not installed. What gets installed by default is 'postfix' and that has a 'sendmail' command, which is a compatibility layer.

---

### Post by HermanAB on 2015-01-09
Fortunately for you, it is not really sendmail, but rather a postfix based program that imitates sendmail.

For details, go to postfix.org and start reading.  Good luck - you'll need it.

BTW, if you want a mail server that is easy to install and just works, try citadel.  It takes about 30 minutes to run the easy install script.

---

### Post by SeijiSensei on 2015-01-09
If you install sendmail with "sudo apt-get install sendmail" then you get sendmail, not postfix.  

OP, it looks you didn't run "apt-get install" with the sudo prefix.  As an ordinary user, you cannot install software.  You need to gain administrative rights by using sudo and entering your login password when prompted.

---

