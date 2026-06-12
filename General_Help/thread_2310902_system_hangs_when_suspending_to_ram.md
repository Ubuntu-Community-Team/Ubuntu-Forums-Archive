---
title: "system hangs when suspending to ram"
date: 2016-01-22
forum: General Help
---

### Post by ryadav on 2016-01-22
Hello does anyone know how I can track down why my system hangs with I try to suspend to ram?

I am using kubuntu, I've logged bugs with kde and the response I got is that it might not be kde but something else? no one had looked at this bug for weeks!

what log files can I search through that might help me figure out if it's hardware related or system related?

In the past I didn't have an issues with ubuntu (kde) 14.10, I went weeks only suspending to RAM, now I just get a hangs.

---

### Post by Doug S on 2016-01-22
do you have a /var/log/pm-suspend.log file? And if yes, does it provide any insight?

---

### Post by ryadav on 2016-01-22
I looked in there, but everything seems fine other than this error:

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

I also switched back from the Nouveau video drive to a NVidia driver, but this doesn't seem to help much.

---

