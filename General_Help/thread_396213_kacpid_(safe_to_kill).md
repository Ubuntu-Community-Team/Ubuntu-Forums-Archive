---
title: "kacpid (safe to kill?)"
date: 2007-03-29
forum: General Help
---

### Post by ruanza on 2007-03-29
Hi everybody

I noticed that kacpid-work processes are EACH utilizing about 30-40% of cpu time. I reniced them to 19, but it is still slowing down our ubuntu 6.06 server. I would like to know if it is safe to kill -9 the kacpid process altogether or if it is integral to the server. I do not have console access so rebooting with -noacpi isn't going to work for me.

Any ideas? Wouldn't like a kernel panic or anything of the sort (esp since I only have remote access).

Regards

R

---

### Post by acormack on 2007-03-30
ACPI is power management and is not essential.  if you are remote from the system with no access I would think long and hard before switching it off though!!!

FYI this is what I did on my kubuntu laptop to stop and then  restart it.

sudo /etc/init.d/acpid stop
 * Stopping ACPI services...                                                                                                                                                                                     [ ok ]

sudo  /etc/init.d/acpid start
 * Loading ACPI modules...                                                                                                                                                                                       [ ok ]
 * Starting ACPI services...                                                                                                                                                                                     [ ok ]




Alec

---

