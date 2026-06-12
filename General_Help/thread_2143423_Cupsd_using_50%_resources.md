---
title: "Cupsd using 50% resources"
date: 2013-05-09
forum: General Help
---

### Post by mdavies5 on 2013-05-09
Initially I could set up a printer in 13.04 and it worked ok. After a few days I noticed that the cupsd process was using 50% of my processor continuously even though the printer was not switched on. Worse, I cannot open the printer configuration utility. All I get is "There was an error during the CUPS operation: 'server-error-internal-error'.".
I have checked all the relevant conf files but no problems are obvious. I tried the /var/log/cups/error_log file but it was over 10Gb and growing!. I deleted and rebooted to try and open it before it grew too big but it will not log anything now. ANY help would be appreciated. EG Can I delete some conf files and let them be auto generated?

---

### Post by tgalati4 on 2013-05-09
You might have a bad printer queue that is causing cupsd some problems.  Try deleting all printers, reboot, then monitor cpu usage of cupsd and check the log files.  Then add back one printer at a time and test it thoroughly until adding the next printer.  Try printing from several applications, not just using cups test print.

---

### Post by mdavies5 on 2013-05-10
Thanks tgalati4 for prompt response. It did not solve problem but did foce me to find a way to read my error_log using tail. This showed the error as: "File "/usr/lib/cups/notifier/dbus" has insecure permissions". The answer to this problem was found in [COLOR=#333333][FONT=Ubuntu]**Bug #999295 and provided by **[/FONT][/COLOR][Lars Uebernickel (larsu)]("https://launchpad.net/~larsu"):

[COLOR=#333333][FONT=Ubuntu Mono]sudo stop cups[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]  sudo rm /etc/cups/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]subscriptions.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]conf*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]  sudo rm -r /var/cache/cups[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]  sudo start cups

This fixed my problem immediately. This can be marked as [SOLVED]; I don't think I have permissions to do that.[/FONT][/COLOR]

---

