---
title: "Issue installing DraftSight CAD program"
date: 2013-07-18
forum: General Help
---

### Post by mckaymotoworks on 2013-07-18
I have attempted to install Draftsight since 12.10, now running 13.04 and it always hangs toward the end of install, to the point I have to purge the installed files to get Software Center or Software Update to function as it gives the : [FONT=Ubuntu Mono]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)[/FONT]
E: Unable to lock the administration directory (/var/lib/dpkg/)I tried to work with Dassault's support team, they could not pinpointing the issue. Was hoping someone seasoned, possibly running this app successfully could help.

---

### Post by ibjsb4 on 2013-07-18
That usually means that [FONT=Ubuntu Mono]/var/lib/dpkg/[/FONT] cannot be lock because another package manager is using it.  Could you possibility have maybe the 'software center' or 'update manager' open while trying to install it?

You could also try manually unlocking it before installing your package.

```
sudo rm [FONT=Ubuntu Mono]/var/lib/dpkg/lock[/FONT]
```

---

