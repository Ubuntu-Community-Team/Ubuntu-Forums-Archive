---
title: "Service won't start - troubleshooting"
date: 2007-02-07
forum: General Help
---

### Post by beanbrain on 2007-02-07
Hello,

How can I troubleshoot a service that won't start at startup?

I installed PostgreSQL 8.1 via Synaptic and I can see an entry for it as "Database server" in the UI under System|Administration|Services. The checkbox next to the entry is checked.

Based on the setting in /etc/inittab it appears that "2" is my default run level, and when I look in /etc/rc2.d I see "S19postgresql-8.1" (enabled, if I understand correctly).

I've tried to find a log file entry for the startup failure but have come up empty. I checked /var/log/boot, daemon.log, and other files.

Any idea what I need to do to get PostgreSQL running at startup, or how to pinpoint the exact problem?

Thank you!

---

### Post by lloyd_b on 2007-02-07
There should be something in a log file somewhere, but:
```
sudo /etc/init.d/postgresql-8.1 restart
```
should stop and then restart that service.  At that point, if there are any error messages, they will appear in the terminal window (rather than being hidden away in a log file).  Hopefully this will give you a clue as to what's going wrong.

Lloyd B.

---

### Post by beanbrain on 2007-02-07
Hey Lloyd,

Thanks for taking the time to help me out.

I'm not seeing any messages output after restarting--I just enter my password and get a new line--so that seems to be working fine.

For whatever reason it seems to be at startup that Postgres won't do its thing. Once I'm logged in I just use pg_ctl to start it up, but of course I'd prefer that it run automagically at startup (and to understand why it's not working now).

I would expect to see a boot-related log error somewhere, but checking the log files I mentioned turned up nothing.

This was working at one point, and didn't become a problem until I removed and reinstalled Postgres (I removed every reference to it after the initial uninstall, so I don't think that's the problem).

---

### Post by goneskiing on 2007-02-18
*sudo /etc/init.d/postgresql-8.1 restart*

the restart or "start" command should work - but you say you are getting nothing - it sounds like your installation is somehow whacked.    I would remove the postgres package using synaptic - reboot - then reinstall.  when ubuntu installs postgres, it usually is set to in the startup services to be activated.  if not try the init.d  command again.

---

### Post by beanbrain on 2007-02-20
gones,

Yes, it definitely got whacked. I spent days on this, and the Postgres docs were only somewhat helpful (grr).

After uninstalling/reinstalling/reconfiguring more times than I can remember (!), Postgres does start successfully at boot-up. However, it starts the wrong cluster--the one created automatically at installation--and not the user-defined cluster belonging to 'postgres' as instructed by the documentation.

So I have to use pg_ctl to stop the default cluster (the one created at /etc/postgresql/8.2/main/pgdata), and then again to start my cluster (the one I created at /usr/local/pgsql/data).

I wish I could eliminate this extra step, but at this point I'm just glad it's working again. ;)

---

