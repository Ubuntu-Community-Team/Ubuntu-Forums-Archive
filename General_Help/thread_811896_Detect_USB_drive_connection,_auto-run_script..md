---
title: "Detect USB drive connection, auto-run script."
date: 2008-05-29
forum: General Help
---

### Post by ShawnMilo on 2008-05-29
When I plug in a USB drive, I'd like to automatically do some kind of synchronization between it and a folder on the machine.

I don't want to schedule it as a cron job -- I'd like it to automatically happen when the system detects the USB drive connection.

Preferably, I'd like a way to do this as a non-root user, and have the method work on my Mac as well, so I can sync among multiple machines.

Is there a way to do this? If there's no way to do exactly this and I have to schedule a cron job or something, which file(s) should I monitor?

Obviously I can monitor /etc/mtab, but is there some cleaner way? This seems like a dirty hack.

Thanks,
Shawn

---

### Post by ShawnMilo on 2008-11-11
I think it's reasonable to bump this after so long. Some help, please?

Thanks,
Shawn

---

### Post by cbr on 2008-11-16
Hi ShawnMilo

Try take a look at [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

Worked like a charm for me...

/cbr

---

