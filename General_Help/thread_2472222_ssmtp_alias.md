---
title: "ssmtp alias"
date: 2022-02-21
forum: General Help
---

### Post by BigYellowDog on 2022-02-21
I have setup ssmtp using [https://help.ubuntu.com/community/EmailAlerts](https://help.ubuntu.com/community/EmailAlerts) and I can send email on the command line if I specify a recipient.

I can not alias my local user to my Gmail account so that I get email from cron or at jobs.  The mail goes to my local user id 'robf' @gmail.com.  Since this is an invalid Gmail address I get a bounce back message.

I'm seeing this in /var/log/mail.log
> Feb 21 11:57:00 ubuntu sSMTP[497004]: Unable to set robf="account@gmail.com"

---

### Post by schragge on 2022-02-21
Your **/etc/ssmtp/revaliases** should contain something like
```
robf:account@gmail.com:smtp.gmail.com:587
```

---

### Post by BigYellowDog on 2022-02-22
That is exactly what I have in my revaliases file.  Any other suggestions?  Much appreciate any help.

```
[robf@ubuntu] ~ $ sudo cat /etc/ssmtp/revaliases
# sSMTP aliases
#
# Format:       local_account:outgoing_address:mailhub
#
# Example: root:your_login@your.domain:mailhub.your.domain[:port]
# where [:port] is an optional port number that defaults to 25.
#
#root:account@gmail.com:smtp.gmail.com:587
robf:account@gmail.com:smtp.gmail.com:587

```

---

### Post by schragge on 2022-02-22
Use another MTA I guess? Like [dma]("https://packages.ubuntu.com/search?keywords=dma&searchon=names&exact=1&suite=all&section=all"). ssmtp is a nice little MTA, but it was last updated 2009.

---

### Post by BigYellowDog on 2022-02-23
Thanks for the info.  I installed msmtp, it works, but is kinda slow with GMail.  I'll give dma a try.

---

