---
title: "add external USB hard drive"
date: 2019-09-15
forum: General Help
---

### Post by kdmiller45 on 2019-09-15
I added a 300Gig external USB harddrive, but have now swapped it for a 1TB, but it is still showing the old hard drive and space used. what must I do to get the system to recognize the new hard drive spec's

Keith

---

### Post by TheFu on 2019-09-15
Did you mount the partition to a different location using the UUID or new LABEL?
Which file system does it have? Is that the same or different from the old partition?

I'm guessing that if you just connect it and use a GUI to access it via GVFS or GIO (gnome less-than-great-stuff), then Gnome is caching the information somewhere.

---

### Post by Dennis N on 2019-09-15
Absent further details, just speculating here. If you mount by inserting into usb port, the drive mounts under /media/<your-user>/. If you don't eject it properly, the mount point folder might not be deleted on shutdown as it is when using 'eject' or 'safely remove' (and the folder isn't reused next time either - you get a new folder). 

So, in the above scenario, if you see the old hard drive folder just delete it. Next time eject the drive correctly.

---

