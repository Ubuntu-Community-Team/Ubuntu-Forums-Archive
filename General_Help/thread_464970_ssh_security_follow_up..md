---
title: "ssh security follow up."
date: 2007-06-05
forum: General Help
---

### Post by eentonig on 2007-06-05
Hi,

How feasible would it be, to have my system set up, to sent me an email (or a shell prompt) whenever I user successfully authenticates via ssh?

I have a ssh server running at home, and regularly I see connection attempts.

That's ok. Most of them give in after three or four attempt. But occasionally, you have the persistent scriptkiddies who keep trying for hours. And maybe one day will succeed in getting through. In which case I would like to be informed.

Another thing I thought of. Would it be possible to set up a script that regularly scans /var/log/auth.log to look for failed attempts. And if it sees that the same ip address keeps trying to connect '(in a short time frame) with random usernames/password, update iptables to block access from that IP.

---

### Post by nemarasu on 2007-06-05
This may help...

[http://www.faqs.org/docs/securing/chap14sec116.html](http://www.faqs.org/docs/securing/chap14sec116.html)

[http://www.linux-sec.net/Scanner/]("http://www.linux-sec.net/Scanner/")

---

### Post by eentonig on 2007-06-05
Thx,

installed and configured portsentry.

The only problem now is that I can test it from here. I can't do a portscan through the companies FW. And all the online scans I know only scan the host you access them with (logic off course)

---

### Post by reclusivemonkey on 2007-06-05
Although this doesn't answer your question directly, you may find it interesting;

[http://debaday.debian.net/2007/04/29/fail2ban-an-enemy-of-script-kiddies/](http://debaday.debian.net/2007/04/29/fail2ban-an-enemy-of-script-kiddies/)

---

