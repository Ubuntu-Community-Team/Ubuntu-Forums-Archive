---
title: "Postgresql fails to start at start-up"
date: 2008-06-12
forum: General Help
---

### Post by Mateo on 2008-06-12
However, I can start it manually by running

```
sudo /etc/init.d/postgresql-8.3 start
```

I checked /var/log/syslog and there is no appearance of postgresql in that file.  where else do I check for the possible cause?

---

### Post by Mateo on 2008-06-14
bump.

---

### Post by rogier.de.groot on 2008-06-14
Does postgresql show up in the System->Administration->Services (or similar, translating from Dutch here) menu? If so you should be able to enable it from there.
Otherwise install sysvconfig (e.g. "sudo apt-get install sysvconfig") and run it in a shell window (command line) and enabled the postgresql service from there - don't forget to select "Finish" before quiting, or your changes won't be saved.

---

### Post by Mateo on 2008-06-14
does not show up in Services, but it does appear in that utility as enabled.  still not working.  someone have some sympathy and help.

---

### Post by rogier.de.groot on 2008-06-15
Are you really sure it's enabled? Is there some failure message in /var/log/messages related to postgresql?
You could always add a line like "/etc/init.d/postgresql-8.3 start" to the end of the /etc/rc.local file (but before the "exit 0" line).

---

