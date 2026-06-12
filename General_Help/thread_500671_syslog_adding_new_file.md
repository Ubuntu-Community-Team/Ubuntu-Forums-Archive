---
title: "syslog: adding new file"
date: 2007-07-14
forum: General Help
---

### Post by l_b on 2007-07-14
Hi,

I recently installed AVG virusscanner on my ubuntu laptop. And I can see the activity of AVG in my /var/log/syslog file.
```
Jul 14 14:12:47 Manuel avgscan[10273]: ERROR: access denied
Jul 14 14:12:48 Manuel avgscan[10367]: Starting AVG Anti-Virus in daemon mode. 
Jul 14 14:12:48 Manuel avgscan[10368]: AVG Anti-Virus Daemon started.
Jul 14 14:12:48 Manuel avgscan[10367]: Starting AVG Anti-Virus on-access scanner. 
Jul 14 14:12:48 Manuel avgscan[10369]: AVG Anti-Virus on-access scanner started
Jul 14 14:13:38 Manuel exiting on signal 15
Jul 14 14:13:38 Manuel syslogd 1.4.1#20ubuntu4: restart.
Jul 14 14:13:38 Manuel avgscan[10369]: ERROR: access denied
Jul 14 14:13:40 Manuel avgscan[10447]: Starting AVG Anti-Virus in daemon mode. 
Jul 14 14:13:40 Manuel avgscan[10448]: AVG Anti-Virus Daemon started.
Jul 14 14:13:40 Manuel avgscan[10447]: Starting AVG Anti-Virus on-access scanner. 
Jul 14 14:13:40 Manuel avgscan[10449]: AVG Anti-Virus on-access scanner started
```

Is it possible to put the avgscan messages in a seperate file? I looked at /etc/syslog.conf but I couldn't find a way to specifiy that the avgscan messages should go to: (for example) /var/log/avg

Does anyone know a way to accomplish this?

Thanks in advance!

---

### Post by geraldm on 2007-07-14
Most programs that log have options on where to send the log messages.
Look in that package for documentation,   It might be a configuration file,
or a parameter to be passed to the executable on the command line.
If there is no such option or documentation, contact the package maintainer.

Gerald

---

