---
title: "CUPS-PDF PostProcessing script is not running"
date: 2013-04-04
forum: General Help
---

### Post by ycp101 on 2013-04-04
I am using Ubuntu 10.04. CUPS-PDF works great. However I wanted to change the output filename. So I followed those steps as described in [http://www.debianadmin.com/howto-install-and-customize-cups-pdf-in-debian.html](http://www.debianadmin.com/howto-install-and-customize-cups-pdf-in-debian.html)

However, I found the post processing script file, [COLOR=#000103][FONT=Arial]cups-pdf-renamer, never runs. It runs when I run it manually from command line. I struggled to fix it by myself for a few hours. I could not find anything helpful. I also found errors in CUPS log file, /var/log/cups/error_log.

[/FONT][/COLOR]```
E [04/Apr/2013:19:58:58 +0900] Unknown directive SystemGroup on line 3 of /etc/cups/cupsd.conf.
E [04/Apr/2013:19:58:58 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
```
[COLOR=#000103][FONT=Arial]
[/FONT][/COLOR]

---

