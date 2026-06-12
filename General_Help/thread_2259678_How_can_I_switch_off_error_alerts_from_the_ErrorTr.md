---
title: "How can I switch off error alerts from the ErrorTracker"
date: 2015-01-06
forum: General Help
---

### Post by Ulf_Dunkel on 2015-01-06
Every now and then, I see alerts on some of my Ubuntu clients which state that Ubuntu has experienced an internal error. The alert box has a checked option to send an error report, plus an unchecked option to "Ignore future errors of this type".

I would like to totally suppress alerts of this kind, and simply reboot Ubuntu if necessary. Can I somehow adjust or totally deactivate the ErrorTracker via CLI?

---

### Post by Ulf_Dunkel on 2015-03-18
I seem to have found a solution on my own, but I'd be glad to receive your opinions on this strategy.

I have deactivated and switched off the services Apport and Whoopsie on my Ubuntu clients for now, doing these steps:

$ sudo nano /etc/default/apport

---snip---
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
**enabled=0**
---snap---

$ sudo nano /etc/default/whoopsie
   
---snip---
[B]   
[General]
report_crashes=false

report_metrics=false[/B]
---snap---

$ sudo mv /etc/init/apport.conf /etc/init/apport.conf.disabled
sudo mv /etc/init/whoopsie.conf /etc/init/whoopsie.conf.disabled

---

