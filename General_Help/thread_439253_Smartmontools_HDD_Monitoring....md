---
title: "Smartmontools: HDD Monitoring..."
date: 2007-05-10
forum: General Help
---

### Post by RichGuk on 2007-05-10
Hello,

I'm having a bit of trouble getting the smartd to send a test email out to my email address. I have mailx installed and I can send mail using the "mail" command, i.e. "mail [email]me@domain.com[/email]" then typing a subject when prompted and then a message and then pressing Ctl + D and a CC, and it seems to send fine but when I attempt to do it in the smartd.conf file it just fails.

This is my /etc/smartd.conf

```
DEVICESCAN -S on -o on -a -I 194 -me@domain.com -M test -M exec /usr/bin/mail -s (S/../.././02|L/../../6/03)
```

Tried without the -M exec, same.

Smartd is enabled in /etc/default/smartmontools, start_smartd=yes


I was wondering if anyone had an idea on the problem?

Thanks,

Richard

---

### Post by RichGuk on 2007-05-10
*bump*

---

### Post by ectospasm on 2007-05-19
I suggest something simple like ssmtp;  mailx and mailutils seem to be too heavyweight for such a simple purpose.  I'm trying to get "/etc/init.d/smartmontools start" to even start smartd...

---

