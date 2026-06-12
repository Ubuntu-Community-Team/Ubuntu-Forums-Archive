---
title: "How can I see startup events?"
date: 2013-06-09
forum: General Help
---

### Post by tigerjack89 on 2013-06-09
Hey there.
As the title, is there any way to see the startup events? 
During the OS load I see a [fail] somewhere, but I can't read to what it refers.

Thanks in advance

---

### Post by deadflowr on 2013-06-09
logfiles are located in /var/log.

You probably want to look at the dmesg logfile.
Or syslog.
Or kern log.

Or whatever other logfiles there are.

---

### Post by tigerjack89 on 2013-06-09
> **deadflowr said:**
> logfiles are located in /var/log.

You probably want to look at the dmesg logfile.
Or syslog.
Or kern log.

Or whatever other logfiles there are.
OT: how can I search the exact word "[fail]" in all the files in a directory?

BTW thanks for your response, I find the problem

```

/var/log/boot.log: * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                           [fail]

```

---

### Post by deadflowr on 2013-06-09
Do you have a network printer?

CUPS is a printer tool, which can be used for network printing.

---

### Post by tigerjack89 on 2013-06-09
> **deadflowr said:**
> Do you have a network printer?

CUPS is a printer tool, which can be used for network printing.
I read this on the interneet, but no, I haven't a network printer, just a locale one :S

---

### Post by tigerjack89 on 2013-06-10
So, how can I fix the error? Thanks in advance guys :)

---

### Post by tigerjack89 on 2013-06-26
up! any idea on this problem?
Thanks in advance :)

---

