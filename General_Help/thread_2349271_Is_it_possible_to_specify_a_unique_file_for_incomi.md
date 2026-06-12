---
title: "Is it possible to specify a unique file for incoming Syslog events?"
date: 2017-01-12
forum: General Help
---

### Post by markiemark2017 on 2017-01-12
[COLOR=#242729][FONT=Arial]I am using a number of propriety devices which sends syslog events to a ubuntu machine (based on IP and default port). By default, these messages are ending up in /var/log/syslog. I am unable to configure a different file target on the device, apart from the server IP address.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there a way to configure syslog so that external events are kept in a separate file?[/FONT][/COLOR]

---

### Post by ian-weisser on 2017-01-12
On the machine receiving the log entries, create an rsyslogd config file in /etc/rsyslog.d/
See 'man rsyslogd' for a lot of information on how to configure it.

---

