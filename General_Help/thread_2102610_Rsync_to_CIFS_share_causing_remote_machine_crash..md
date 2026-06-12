---
title: "Rsync to CIFS share causing remote machine crash."
date: 2013-01-07
forum: General Help
---

### Post by PinkFloyd102489 on 2013-01-07
Hello,

I have a script set up at work to rsync my work directory on my Ubuntu laptop to my work Windows desktop, which is connected to the laptop via a CIFS share.

Lately, it will get about halfway through the rsync before the Windows machine blue screens and crashes. I'm not sure if this is an issue with Linux/Rsync or Windows, so I'm trying to solve at least one half of it.

Has anyone else seen this?

```
rsync -auvh --exclude 'HY-MA-MI' work/ /media/work
```

---

### Post by tgalati4 on 2013-01-07
Windows Blue Screen?  Yes I've seen it several times.  Try rsyncing to an Ubuntu desktop or to Ubuntu One on the net.

Check your log files in /var/log.  Check for weird file names for any files created in the last week.  Use the --stats switch, and there may be other switches to increase the verbosity of rsync so you can pinpoint where it is failing.

---

