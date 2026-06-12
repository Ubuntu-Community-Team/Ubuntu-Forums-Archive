---
title: "Why does Anacron need an MTA?"
date: 2019-05-08
forum: General Help
---

### Post by stepheny on 2019-05-08
I am using Ubuntu 18.10 and have added a short script to anacrontab. Now I get this log warning from Anacron:

> Can't find sendmail at /usr/sbin/sendmail, not mailing output

I receive messages from other utilities (printer jobs, usb connected etc) via the usual Gnome messages. Why is Anacron insisting on sendmail, and do I have to install sendmail (or postfix) just for Anacron?

---

### Post by TheFu on 2019-05-08
> **stepheny said:**
> I am using Ubuntu 18.10 and have added a short script to anacrontab. Now I get this log warning from Anacron:



I receive messages from other utilities (printer jobs, usb connected etc) via the usual Gnome messages. Why is Anacron insisting on sendmail, and do I have to install sendmail (or postfix) just for Anacron?

Cron has always sent output to the MTA, probably since 1970.  I find it handy, but I setup all my systems to send email out to the central email server. 
Unrelated, but I find it very handy to be able to shoot off a quick email somewhere from a shell on any system.

cron, anacron, at, batch are all part of the cron tools which use email to send the stuff normally send to stdout+stderr somewhere.

BTW, sendmail isn't required. All the other MTAs provide a "sendmail" compatible setup and work just fine.

If you don't want **any** output from cron or anacron, then you can redirect all the output to /dev/null, but then you'll never know what happened or if there were problems.  It is most common to redirect stdout to /dev/null, but allow stderr to be emailed, so errors are seen.

---

### Post by HermanAB on 2019-05-09
Why?  Because all software grows until it can send email.

---

### Post by stepheny on 2019-05-09
And older software sends a fax?

---

### Post by TheFu on 2019-05-09
> **stepheny said:**
> And older software sends a fax?

No.  Email has been around longer and is much easier to use than fax.

Or was that a joke?

---

### Post by stepheny on 2019-05-11
It was a joke. But seriously the fax has been around a lot longer than email. Since 1846 in fact [https://en.wikipedia.org/wiki/Fax](https://en.wikipedia.org/wiki/Fax)

---

