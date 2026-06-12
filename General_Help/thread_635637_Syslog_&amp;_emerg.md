---
title: "Syslog &amp; emerg?"
date: 2007-12-08
forum: General Help
---

### Post by dyntryx on 2007-12-08
This may be a silly question, but I don't understand why *.emerg is not working properly in my syslog.  Please correct me if I'm doing something wrong here, as I'm still learning.  This is actually for a class I'm taking.  The class uses Fedora, but I'm using Kubuntu since I'm more familiar with it; anything that can be done in Fedora should be possible in Kubuntu, so I'd rather learn the "Debian/Ubuntu" way. :)

From /etc/syslog.conf:
```
#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *
```

From command line:
```
# logger -p user.emerg -t TESTING Emergency message text.
```

As I understand it, this is supposed to use *wall* to send the message to all logged in users.  So, I logged in from another console (Ctrl+Alt+F2).  Then I went back to KDE (Ctrl+Alt+F7).  I opened a virtual console and ran this command.  I went back to the other console (Ctrl+Alt+F2) and the message is not there.

Also... yes, syslog is running. :)
```
# ps aux | grep [s]yslog
syslog   17930  0.0  0.0   1912   736 ?        Ss   22:05   0:00 /sbin/syslogd -u syslog
```

Commands like this work fine:
```
# logger -p user.info -t TESTING This is a logging test.
# tail /var/log/messages
... unnecessary output ...
Dec  8 22:28:42 hostname TESTING: This is a logging test.
```

Any suggestions? :-?

---

