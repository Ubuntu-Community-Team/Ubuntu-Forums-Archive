---
title: "ifrename called on startup, but ifrename never installed"
date: 2006-07-25
forum: General Help
---

### Post by afoglia on 2006-07-25
I don't recall ever installing ifrename, but there's now a startup script /etc/rcS.d/S40ifrename that's getting called on startup and giving the error message: "/sbin/ifrename: no such file or directory"

I have no idea what package would have created this script.  It doesn't appear in any breezy or dapper packages.  I did just update my system today, but none of the packages were about ifrename.

I'll just delete, but I'd like to know if others are seeing it as well.

---

### Post by inspired on 2006-07-28
Hi there,
Yes, I also get this error.
Same story... /etc/rcs.d/S40ifrename is trying to call /sbin/ifrename which does not exist and this generates an error.

QUESTION
Does it cause your boot process to hang (until you press CTRL-C to move on to the next step) ?

Mine is hanging... but at the step just before this one mentioned here.
It hangs on "Starting Enterprise Volume management system". I then push CTRL-C and it moves on to the Ifrename issue (which does not hang the system at this point)

Thanks,

Jonathan

---

### Post by The Chef on 2006-07-29
Yes, I get the same message.  However, I only get it when I have my D-Link AirPlus WiFi card installed in my laptop PCI slot.  So, maybe, it is something to do with ndiswrapper / hotplug / constant-wireless-related-linux-irritation.

---

### Post by afoglia on 2006-07-30
> **inspired said:**
> 
QUESTION
Does it cause your boot process to hang (until you press CTRL-C to move on to the next step) ?

Mine is hanging... but at the step just before this one mentioned here.
It hangs on "Starting Enterprise Volume management system". I then push CTRL-C and it moves on to the Ifrename issue (which does not hang the system at this point)


No.  Mine doesn't hang.  It sounds like the Enterprise Volume Management system is your bigger problem.

---

### Post by stanwebber on 2006-08-07
i confirm this behavior.  i disabled splash yesterday & have started noticing this error in the startup messages.  i upgraded my system from hoary > breezy > dapper with minimal issues otherwise

---

