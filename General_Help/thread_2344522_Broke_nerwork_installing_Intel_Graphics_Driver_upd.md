---
title: "Broke nerwork installing Intel Graphics Driver updater"
date: 2016-11-26
forum: General Help
---

### Post by moteprime on 2016-11-26
Hi please help.
I installed the Intel Graphics updater from Intel, it broke my network entirely, theres no devices in networkmanager.
The driver wouldn't run because of missing lib of kinds, so i unistalled it, but my network are still broken. I'm typing this from a live session.
lspci lists the network devices ok, but the system doesn't see them. I tried starting up on older kernels but the doesn't help so i guess it above kernel level.
Are there something i can reinstall, or otherwise do to get it running again?
Thanks

---

### Post by moteprime on 2016-11-28
Can't i even reinstall the system without deleting everything?

---

### Post by howefield on 2016-11-28
> **moteprime said:**
> Can't i even reinstall the system without deleting everything?

Not sure that you couldn't fix the networking issue without a reinstall but yes you can reinstall with deleting everything if what you mean by that is your /home folder, mounting the existing / partition for during the reinstall without marking it for formatting will delete everything except /home.

Presumably Ubuntu 16.04 as per your profile ?

---

### Post by moteprime on 2016-11-28
@howefield Thanks for responding.

I'm on a Thinkpad L450 core i5. and I figure that some part of the intel graphics driver broke some other intel driver that controls the networks. Isn't it possible to reinstall that part. -I'm not especially afraid of screwing the system up so much, as it's already not working very well.

---

### Post by howefield on 2016-11-28
Well the way I see it is that you either start a thread in the [Networking & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") forum along with the information from the wireless script as described in [this thread]("https://ubuntuforums.org/showthread.php?t=370108") (done whilst in the borked system) or you do a reinstall.

Personally I'd give the former a try and if no quick(ish) response I'd reinstall as above leaving the /home folder unharmed.

---

### Post by moteprime on 2016-11-28
Thanks. I'll give it a try.

---

