---
title: "SUSPEND fails on Lenovo e11 (18.04LTS)"
date: 2018-04-27
forum: General Help
---

### Post by tolito-cr on 2018-04-27
Hi there… I’m an amateur user, yet enthusiast for years with many distros of Ubuntu. I did a fresh install yesterday of the new LTS release, and everything worked fine out of the box except for the SUSPEND feature.

I understand in this version it is set by default to suspend when closing the lid, however, nothing happens when I close it. Moreover, nothing happens either when I select "suspend when closing lid" in the Tweak Tool or when I run $ systemctl suspend.

The outcome is:
Operation inhibited by “UpdateManager” (PID 3019 “update-manager”, user edu), reason is “Updating System”.
Please retry operation after closing inhibitors and logging out other users.
Alternatively, ignore inhibitors and users with ‘systemctl suspend -i’.

Is this a bug for this version or something particular to Lenovo models? I am using a Lenovo e11, Intel Celeron N3150 Quad-Core Processor, 8GB RAM, 128GB SSD, Webcam, Bluetooth, 802.11ac, HDMI.

Thanks!

---

### Post by gocarlos on 2018-05-14
Having the same problem...

there is an open bug report for that

---

