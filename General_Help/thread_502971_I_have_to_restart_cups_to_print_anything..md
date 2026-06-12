---
title: "I have to restart cups to print anything."
date: 2007-07-17
forum: General Help
---

### Post by tgrzejsz on 2007-07-17
Hi,
I use kubuntu Feisty. Each time I want to print something I can see a nice KJobViewer window popup with a new printing job with a status "Processing". Then I can wait forever and nothing happens. No indication in logs of anything going wrong. Restarting cups server (/etc/init.d/cupsys restart) works like magic, but I don't know what to think about this feature. Restarting printing server every time I want to print something seems a bit unproductive.

Thanks for any help,
Tomek

---

### Post by ajgreeny on 2007-07-17
Something has obviously gone wrong here as I run the same system without any problems, and printing seems to work faultlessly.  Have you trieed uninstalling completely cups and then reinstalling again?  It might be worth a try.
PS  Has it always been like this from install, or has it just started playing up after installing something?

---

### Post by tgrzejsz on 2007-07-19
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/bugs/45099](https://launchpad.net/bugs/45099) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **ajgreeny said:**
> Something has obviously gone wrong here as I run the same system without any problems, and printing seems to work faultlessly.  Have you trieed uninstalling completely cups and then reinstalling again?  It might be worth a try.
PS  Has it always been like this from install, or has it just started playing up after installing something?

Reinstalling CUPS has no effect. I still need CUPS restart before any print job. I've set a cups logging level to debug2 and tried to print something. Contents of /var/log/cups/error_log after that try are attatched. I can see nothing interesting in the logs. System tries to print something and then stops. Then repeatedly cups is queried for status.
My system had been installed as Hoary and then it has been updated every half a year. For sure I have already had my problems in Dapper, I don't remember how it was before.
One interesting thing is that when I print a test page it says "Printed using CUPS v1.1.x" which makes me think this problem may be related to an already filed and rather old bug (without a solution).

---

