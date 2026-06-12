---
title: "Trying to access gpsd from a script in cron"
date: 2016-08-23
forum: General Help
---

### Post by NeillHog on 2016-08-23
I have a GPS module running on a USB port. 
Once the server is running I can do sudo gpsd /dev/ttyUSB0 -F /var/run/gpsd.sock  and then run my python script that uses gpsd to continuously read GPS data.

I have added gpsd /dev/ttyUSB0 -F /var/run/gpsd.sock to roots cron and it works. After a reboot I can run my python script and I receive the GPS data.

But all attempts to start my python script in the cron fail. It doesn't matter if I try to start it in root's cron or in the cron from my normal user.

Maybe cron is the completely false way to go. Maybe I should be using init.d. I am willing to try whatever the experts suggest. I am happy with any help I receive.

Thank you
Neill

---

### Post by SeijiSensei on 2016-08-23
Try adding the command "gpsd /dev/ttyUSB0 -F /var/run/gpsd.sock" to /etc/rc.local above the "exit 0" line.  The contents of /etc/rc.local is run at the end of the boot process.

Notice there is no "sudo" if you use this approach as rc.local is run with root privileges.

---

### Post by NeillHog on 2016-08-25
Thank you for that suggestion.
Unfortunately it did not work.

I have things working by:
- starting gpsd first when it is needed by my script and 
- having a "sleep 60" in the cronjob so that the system has time to do whatever it needs to do before my python script is started.

I am not happy with this solution as I would prefer to know what the prerequisite is and wait for specifically that.
I am still looking.

---

### Post by SeijiSensei on 2016-08-25
Maybe root doesn't have a path to gpsd by default.  Try replacing "gpsd" in rc.local with /complete/path/to/gpsd and see if that works better.

---

