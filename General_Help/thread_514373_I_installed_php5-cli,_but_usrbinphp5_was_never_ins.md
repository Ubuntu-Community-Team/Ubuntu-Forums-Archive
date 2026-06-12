---
title: "I installed php5-cli, but /usr/bin/php5 was never installed."
date: 2007-07-31
forum: General Help
---

### Post by starkruzr on 2007-07-31
What the heck happened?

I want to use KTorrent's web UI, but it requires me to tell it where the PHP binary is.  The problem is there IS no php binary without php5-cli.  More accurately, there appears to STILL be no php binary even WITH php5-cli.

It created a /usr/bin/php link, which links to /etc/alternatives/php, which links to /usr/bin/php5... which doesn't exist.

---

### Post by hangthedj on 2007-07-31
> **starkruzr said:**
> What the heck happened?

I want to use KTorrent's web UI, but it requires me to tell it where the PHP binary is.  The problem is there IS no php binary without php5-cli.  More accurately, there appears to STILL be no php binary even WITH php5-cli.

It created a /usr/bin/php link, which links to /etc/alternatives/php, which links to /usr/bin/php5... which doesn't exist.
you need to install php5-cgi

---

### Post by starkruzr on 2007-07-31
Yeah, that didn't help.  :confused:

---

### Post by starkruzr on 2007-08-01
Okay, I actually got it installed (curiously, installing php5-cgi seemed to uninstall php5-cli), but now it gives me an Internal Server Error every time I try to login.

---

