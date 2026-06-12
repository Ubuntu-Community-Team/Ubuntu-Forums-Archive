---
title: "Ubuntu 14.04 stopped all logging - sudo tail -f /var/log/syslog fails"
date: 2014-07-28
forum: General Help
---

### Post by dcb-09 on 2014-07-28
Hi, I unfortunately installed these tweaks: 

[http://www.noobslab.com/2013/10/enable-laptop-mode-and-other-tweaks-to.html](http://www.noobslab.com/2013/10/enable-laptop-mode-and-other-tweaks-to.html)

This tweak killed logging apparently: [B]Second tweak is to stop access to HDD for log files. If you are in single user system, probably you don't need log file like when this directory/file was accessed last time.
[/B]
I cannot undo them and no there is no system logging. I need system logging to work with my weewx software. This command no longer works and comes back with no such file or directory:

[COLOR=#000000][FONT=Courier New]sudo tail -f /var/log/syslog[/FONT][/COLOR]

Please advise how to "get back to normal" and restart system logging. I am not a geek but a newbie :-)

Thanks!

WH3080

---

