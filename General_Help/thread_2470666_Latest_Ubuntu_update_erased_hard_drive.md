---
title: "Latest Ubuntu update erased hard drive"
date: 2022-01-07
forum: General Help
---

### Post by Richard-S on 2022-01-07
Yesterday I updated Ubuntu 18.04. After I re-booted, Ubuntu would not load. I examined the hard drive and the Ubuntu partition was still there but it was empty. The update process appears to have erased the contents of the partition.

I always make a new Timeshift back-up before an update, so all was restored in a few minutes, but this was weird.

Richard

---

### Post by KBar on 2022-01-07
Which packages were updated exactly? I very much doubt it was because of the update. Post the relevant parts of */var/log/apt/history.log* here.

---

### Post by Richard-S on 2022-01-07
I don't have the history.log file as I reloaded Ubuntu from a back-up made before the update.

The update consisted of:

Apache HTTP server ...
and all of the files associated with the Linux kernel 4.15.0

Richard

---

### Post by QIII on 2022-01-07
Unfortunately, you have scraped the vellum so completely that you do not even have a palimpsest from which to reconstruct what happened.

But I can say that it would be vanishingly rare for an update to wipe a drive.  Is there anything else you might have done, such as issuing a dd command with the wrong device?

---

### Post by Richard-S on 2022-01-07
I shall try the update again and see what happens.

Richard

---

