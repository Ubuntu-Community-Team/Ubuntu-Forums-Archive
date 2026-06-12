---
title: "Ubuntu won't stay shut down"
date: 2008-05-18
forum: General Help
---

### Post by Talon2 on 2008-05-18
I've been running Ubuntu since Dapper.  I've never seen this problem until 8.04 LTS.

The problem:  When I select "Shut Down" from the "Quit" menu Ubuntu proceeds to shut down but it will not stay down.  Generally it will come back to life and reboot within about 2 seconds of shut down but sometimes it takes a while then the system comes back to life and reboots.  Unplugging the electical cord is the only way to keep the system off after a shut down.

I'm searching for solutions.

TIA

---

### Post by dpbklyn on 2012-09-28
I am having this same problem, but with Server 12.04....CLI only.

---

### Post by doktorOblivion on 2012-09-28
Have either of you performed a dmesg to see if any errors are thrown?
Or just cat /var/log/syslog.

---

### Post by doktorOblivion on 2012-09-28
Talon2, have you check to see if you BIOS needs to be upgraded for the later versions of Linux.  Something to investigate.  I would check out all ACPI requirements for your machine and whether this may have changed across the Ubuntu releases and affected your BIOS somehow.

---

### Post by CharlesA on 2012-09-28
Back to sleep you go old thread...

---

