---
title: "tmpwatch or its equivalent for ubuntu?"
date: 2006-07-05
forum: General Help
---

### Post by ktneely on 2006-07-05
I am looking for a utility that does something similar to tmpwatch*

I can set /tmp to delete whenever I reboot, but this server is running as my firewall and I do not plan to reboot it very often.

I am looking for something I can run as a crontab and that deletes based on lack of use after a certain, specified time, as tmpwatch does.

* for reference:  [http://www.die.net/doc/linux/man/man8/tmpwatch.8.html]("http://www.die.net/doc/linux/man/man8/tmpwatch.8.html")

---

### Post by Appolusionist on 2006-07-07
> **ktneely said:**
> I am looking for a utility that does something similar to tmpwatch*

I can set /tmp to delete whenever I reboot, but this server is running as my firewall and I do not plan to reboot it very often.

I am looking for something I can run as a crontab and that deletes based on lack of use after a certain, specified time, as tmpwatch does.

* for reference:  [http://www.die.net/doc/linux/man/man8/tmpwatch.8.html]("http://www.die.net/doc/linux/man/man8/tmpwatch.8.html")

tmpreaper is what you are looking for and you can set it with cron.

---

### Post by ktneely on 2006-07-07
> **Appolusionist said:**
> tmpreaper is what you are looking for and you can set it with cron.

That's the stuff!  Thank you.

---

