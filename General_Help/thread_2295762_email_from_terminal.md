---
title: "email from terminal"
date: 2015-09-21
forum: General Help
---

### Post by aaron27 on 2015-09-21
I am hoping someone here has used this setup. Linux 12.04 just running  terminal and then Groundworks monitoring installed (as a virtual  machine) Everything is setup for Groundworks to function correctly  however we are not recieving email alerts - I am assuming we need some  sort of email client setup however this isnt something ive installed and  setup in terminal before (we cannot use a GUI because this breaks our  Groundworks setup).
 
I can install sendmail and postfix but im not sure a) if these are what i need or b) how to configure them without a GUI

---

### Post by nerdtron on 2015-09-21
Postfix is needed to send emails (I assume you want alert emails from the server). With that, you'll need to have a valid email account and a mail relay. Basically, you'll configure postfix to use an email/password to login to the remote email server and then be able to send email. Another method is for internal mails only, like for the local intranet emails (you still need a machine acting as an email server, this can be the groundworks machine itself).

---

### Post by aaron27 on 2015-09-21
Excellent thank you very much, we  do want emails from the server yes.  Will try it now, have been googling and found setup instructions so  fingers crossed.

---

### Post by mastablasta on 2015-09-21
I am using sSMTP and gmail for that. I chose it because it is easy to setup. here is how you set it up: [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

you can use another mail server as well.

---

### Post by nerdtron on 2015-09-21
> **mastablasta said:**
> I am using sSMTP and gmail for that. I chose it because it is easy to setup. here is how you set it up: [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

you can use another mail server as well.

I've tried SSMTP too with a gmail account. It's a good way to test sending emails from your server via your gmail account. However, after about 2 months, the gmail account was lockedby google, saying it was sending spam.

---

### Post by aaron27 on 2015-09-21
I will stick with what I know and go with postfix (have setup in GUI before so know roughly what to look for) I dont want to over-complicate things or risk having account switched off for suspected spamming

---

### Post by mastablasta on 2015-09-22
> **nerdtron said:**
> I've tried SSMTP too with a gmail account. It's a good way to test sending emails from your server via your gmail account. However, after about 2 months, the gmail account was lockedby google, saying it was sending spam.

same here (I created separate Google account) - it got blocked. however, reinstalling the OS I realised that maybe it could have been considered spam since cron was sending some useless messages before. anyway it is not sending them now. it's been almost 5 months and all is well. I just get email about unattended updates. nothing else.

---

### Post by aaron27 on 2015-09-22
Thank you for the alternative, i have just installed and (tried) to configure postfix. So hopefully emails will start coming through

---

### Post by aaron27 on 2015-09-24
Right so I did that but somehow I have got emails trying to send from ```
[EMAIL="emailaddress@hostname.domainname.co.uk"]emailaddress@hostname.domainname.co.uk[/EMAIL]
``` instead of ```
[EMAIL="emailaddress@domainname.co.uk"]emailaddress@domainname.co.uk[/EMAIL].
```

I believe this means it has been setup as a subdomain? But I can't find where  I would have set that to correct it....any suggestions?

---

