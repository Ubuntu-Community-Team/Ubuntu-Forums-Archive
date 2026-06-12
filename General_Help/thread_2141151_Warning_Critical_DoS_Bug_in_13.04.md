---
title: "Warning: Critical DoS Bug in 13.04"
date: 2013-05-01
forum: General Help
---

### Post by iaw4 on 2013-05-01
I know a "critical bug" is a strong statement, but I think this one qualifies.  by default, X creates the .xsession file.  most of the time, it is fine---except that it can completely overflow the partition.  this happens due to gstreamer in my 13.04 ubuntu (it was ok in 12.10).  in particular, after about 100GB of messages in .xsession like this,

GStreamer-CRITICAL **: gst_bus_timed_pop_filtered: assertion `timeout == 0 || bus->priv->poll != NULL' failed

the system then comes to a halt when it runs out of space on the partition.  lsof tells me that gstreamer plugs into all sorts of other processes, which means that even deleting the .xsession file does not fix the problem.  basically, it seems to require a reboot.

I would think this would be critical bug.

I tried to change in /etc/X11/Xsession

exec >> /dev/null 2>&1  ## iaw-change to remove huge Xsession.log file from $ERRFILE

but this did not work.  I tried a couple of other fixes, but none worked.  if anyone has a solution, please let me know.  right now, I am afraid to start any music.

/iaw

---

### Post by iponeverything on 2013-05-01
its only a DoS in the way that driving over a nail on the way to work is a DoS..

This is more like a routine case of excessive logging..

you might try symlinking the log file to /dev/null..

---

### Post by iaw4 on 2013-05-02
not a solution.  .xsession-errors is always deleted and recreated.

I think everything that can force a system to shut down all processes and reboot (without voluntary user choice) is a critical DoS.  in Xsession, there is even a 

"truncate ERRFILE if it is too big to avoid disk usage DoS"

unfortunately, this is only on reboot.  it works for minor fillup over length periods of time that can be cured between reboots.  it is not capable of dealing with rapid fillups, e.g., through the gstreamer spam.

---

### Post by iaw4 on 2013-05-02
another question---how do I restart the X server?  ctrl-alt-backspace does not work for me.  (maybe it's the apple keyboard.)  I also don't know how to get to virtual consoles any more---ctrl-alt-F1 also does not work.

Xsession does not seem to be executed.  I put an "echo 'IAW'" at the top and looked in all the log files in /var/log/*.log --- it never shows up there.  no wonder that my attempts to tinker with it to suppress creation of .xsession-errors does not work.  where is .xsession-errors actually controlled under 13.04?

right now, I am rebooting for test.  yikes.



/iaw

---

### Post by iaw4 on 2013-05-02
here is how to force a system reboot: open rythmbox.  go to radio.  click on "Absolute Radio (Modern)" or some other station.  at this point, watch .xsession-errors grow huge and crash your system.

---

### Post by miguelnegrao on 2013-05-14
I have the some problem, plus I use btrfs, which means that when I run out of space I can't even delete files... How do we fix this ? Has this bug been reported ?

---

