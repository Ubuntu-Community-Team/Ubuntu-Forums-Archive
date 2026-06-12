---
title: "Ubuntu 12.04 Headless Server - Unresponsive"
date: 2013-08-08
forum: General Help
---

### Post by pMn6RfW on 2013-08-08
Hello All,

I've been trying to find an answer by searching the forums but can't seem to fix the issue i'm having with a headless server running 12.04.
Every now and then, uptime between 5-8 days, my headless server will go un-responsive. No SSH, no ping from another host on the same subnet, same switch. I don't have a external monitor nearby that I can connect the server to. kernel.log or syslog does not show any indication of a crash or why the server stopped working. /var/crash is empty. 
the server runs on a intel i3770k processor, 32GB of Ram, does not have a dedicated video card (nvidia or ati), just whatever's on the motherboard
apart from connecting a monitor or keyboard to diagnose, is there another way I can troubleshoot this problem.

tia for any feedback, etc.

---

### Post by TheFu on 2013-08-08
That is tough to troubleshoot when there aren't any log files.  We need logs, so setting up an rsyslog server on a different machine and sending the logs there as they come in is my only though.

The result sounds like failing hardware - PSU, bad RAM, or a short somewhere.

---

### Post by papibe on 2013-08-08
Hi pMn6RfW.

Start by checking the power saving setting on the BIOS. The machine may be just goes to sleep/hibernation because lack of activity (either keyboard clicks or CPU usage).

Just a thought.
Regards.

---

### Post by pMn6RfW on 2013-08-08
that definitely helps. thanks guys. I'm going to re-purpose an old laptop for a syslog server and check the BIOS, etc. go from there.

---

