---
title: "How to change syslog min log level in Ubuntu 14.04?"
date: 2016-02-20
forum: General Help
---

### Post by roland-logikalsolutions on 2016-02-20
Previously, one used to be able to set the minimum log level in /etc/syslog.conf. There may have even been a command line utility so one didn't have to hack. Today I went looking and it appears someone has taken it upon themselves to redesign syslog. Of course they couldn't be bothered to actually redesign the documentation posted on-line before hurling their creation unto the world. 14.04 has been out since April of 2014 but all of my Web searches turn up doc saying to edit /etc/syslog.conf.

So.

Just how does one setting the minimum application log level in this "wonderful" new version?

For applications under development the default of logging all is fine. When the application is released to production we want to be able to dynamically change minimum log level to DEBUG but have the standard log level be INFO or higher.

---

### Post by roland-logikalsolutions on 2016-02-20
Actually, forget about it. I'm just going to hack it into my logger class. Sweeping changes to fundamental things are _never_ good ideas. Some day the Linux world may learn that.

---

