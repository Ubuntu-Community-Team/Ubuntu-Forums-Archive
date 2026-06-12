---
title: "Prevent /tmp from being cleaned out?"
date: 2008-04-28
forum: General Help
---

### Post by redocpot on 2008-04-28
I'm new to Ubuntu (but been a Linux user for a looong time).
For some reason, I like to keep my crap in /tmp around for as long as possible.
Under other unices, after install I'd just edit tmpwatch under cron.d , and I was all set.
But under Ubuntu, I can't for the life of me figure out where the files in /tmp are cleared.
Can someone point me in the right direction.

// yes, I know I could use /usr/tmp or /var/tmp ; but that's not the question.

---

### Post by Monicker on 2008-04-28
> **redocpot said:**
> I'm new to Ubuntu (but been a Linux user for a looong time).
For some reason, I like to keep my crap in /tmp around for as long as possible.
Under other unices, after install I'd just edit tmpwatch under cron.d , and I was all set.
But under Ubuntu, I can't for the life of me figure out where the files in /tmp are cleared.
Can someone point me in the right direction.

// yes, I know I could use /usr/tmp or /var/tmp ; but that's not the question.

That is handled by the script /etc/init.d/bootclean.  Changing the line which reads TMPTIME=0 to TMPTIME=-1 should do what you want.

---

### Post by Oldsoldier2003 on 2008-04-28
bootclean clears the /tmp on boot. you can turn it off by ```
sudo update-rc.d -f bootclean remove
```

---

