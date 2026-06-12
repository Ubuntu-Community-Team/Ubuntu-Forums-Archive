---
title: "cron help"
date: 2007-04-16
forum: General Help
---

### Post by Witness on 2007-04-16
Hi guys,

I have Ubuntu 6.06 (Dapper Drake) running on an [old dome PPC iMac ]("http://www.dvwarehouse.com/images/comp0302imac_A.gif") that's displaying a contantly updated status page of my help desk ticketing software in Firefox.  When I'm here at the office, I don't want the screensaver to kick in at all, but it's fine when I'm not here, of course.  I figured that creating cron jobs that turn on/off the screensaver option "Activate screensaver when session is idle" at specified times would do the trick, but I have no idea how to find the appropriate commands.  Does anyone have any insight or ideas about this?

Full disclosure:  I'm a Linux and UNIX newb.  Total and complete.

TIA!!

-Wit

---

### Post by raja on 2007-04-16
You can change settings in gconf from the command line with "gconftool-2". So to disable the screensaver for instance, this should work ```
gconftool-2 --set "/apps/gnome-screensaver/idle_activation_enabled" --type bool "false"
``` So put this in script, make it executable and set up a cronjob to run it in the evening. Another script to enable the screensaver should run again in the morning. 
I havent tested this, but it should work.

---

