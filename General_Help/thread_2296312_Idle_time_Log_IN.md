---
title: "Idle time Log IN"
date: 2015-09-25
forum: General Help
---

### Post by mayagrafix on 2015-09-25
I have set my PC to automaticaly start up in the AM. The PC will get as far as the LOG IN screen. Can the Ubuntu OS do anything while at this point? such as  maitenance (HDD defrag for example) or does it just sit there at idle until I log in?

---

### Post by nerdtron on 2015-09-25
I'm pretty sure background services will continue to run even if no one is logged-in. You can still SSH on to the machine or Apache web page is still accessible even when no one is logged in. Although defragging is not need on linux, other custom jobs can be scheduled using the crontab. As long as the machine is up, cron will run scheduled jobs on the background.

---

### Post by Lars Noodén on 2015-09-25
If you want it to something specific in the background upon startup, you can use @reboot in [crontab](http://manpages.ubuntu.com/manpages/trusty/en/man5/crontab.5.html).  Cron jobs that were missed because the computer was turned off will not run, unless you are using [anacron](http://manpages.ubuntu.com/manpages/trusty/en/man8/anacron.8.html) instead.

---

