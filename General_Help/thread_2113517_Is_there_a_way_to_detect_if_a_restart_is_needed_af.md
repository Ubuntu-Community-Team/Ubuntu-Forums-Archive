---
title: "Is there a way to detect if a restart is needed after updates"
date: 2013-02-07
forum: General Help
---

### Post by CaptainMark on 2013-02-07
I would like to configure my ssh banner to display if a restart is necessary to fully update the system on my home server. I know there are some packages (usually kernel related packages) that after being updated will not be used with the updated version until the system is restarted. Is there a way to detect this and add a warning to my ssh banner something like "The system requires a restart to finish updating"?

Many thanks
Mark

---

### Post by smoka on 2013-02-07
Not too sure about how to get he banner to work, but, normally if the following file exists it shows that it needs a reboot:

/var/run/reboot-required

---

### Post by kr651129 on 2013-02-07
From what I've read

/usr/share/update-notifier/notify-reboot-required

Touches a file

"/var/run/reboot-required"

When the system needs to be rebooted, you could mod your script to check for this file every x seconds.

---

### Post by CaptainMark on 2013-02-07
Excellent, good to know, thanks, any script in bash_profile will run on ssh login too so ill put a simple check and echo thingy in there, 

Many Thanks
Mark

---

### Post by CaptainMark on 2013-02-10
I cant seem to find out online so I'll ask here, do you know if this Ubuntu specific or is this standard apt-get behaviour, in other words will it work on my raspberry pi too?

---

