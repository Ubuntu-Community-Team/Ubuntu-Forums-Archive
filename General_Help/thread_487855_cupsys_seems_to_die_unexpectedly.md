---
title: "cupsys seems to die unexpectedly"
date: 2007-06-29
forum: General Help
---

### Post by ashwin_cse on 2007-06-29
Hi,

As said in the subject, this happens in the middle of the printing processs. When this happens the printer no longer accepts prints. It shows as if there are no prints in the queue. My printer is canon ip3000, for which the printer driver is shipped with feisty fawn (my distro). Usually when the print command is given the green led blinks indicating it has received print cmd from pc. This suddenly stops happening when there i give multiple print command . Multiple print cmds are not given in one shot but given after each print is over. I do give multiple print commands because some website dont give their documents in easly printable pdf format or single html format. But they give it in many small html files. Ok, Back to the point, when the printing suddenly stops, i manually restart the cupsys by this cmd in terminal ```
sudo /etc/init.d/cupsys restart
``` . Then printing starrts again.
   One wired thing i noticed is, that in browser window of [http://localhost:631/](http://localhost:631/) . When i click on the administration tab & job tab, it returns 404 error page. This problem fixes when i restart cupsys. In the file /var/log/cups/error_log there are multiple entries which says "no authentication data provided". Further when i click on the administrative tab, it doesn't ask for username & password. Which is usually the case with fedora.
  Should i file a bug report on this. Or am i doing something wrong. I searched bugs.launchpad but found no matching bugs.

with regards,
ashwin

---

