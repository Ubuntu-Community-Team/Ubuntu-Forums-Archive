---
title: "googleearth causes X to crash"
date: 2007-07-15
forum: General Help
---

### Post by dfpd62 on 2007-07-15
Hi Folks

Google Earth seems to crash Xorg on startup in the last week, worked fine for months before.
I suspect a Fiesty upgrade may have caused a problem with my radeon 9200se driver or something?.

Tried reinstalling Google earth and it worked first time, but crashed again after next reboot.

Also looked at updating the radeon driver after reading posts form other people who had the same problem, unfortunatly the latest driver does not cover my card. 

Any ideas welcome
Thanks

Donald.

---

### Post by w4ett on 2007-07-15
Let's check out your 3D rendering:

Copy and paste:

glxinfo

and then:

glxgears         What is your FPS rate?

I use a 9200se with the xorg-ati drivers

Have you reconfigured your xorg.conf lately?...check that the driver is set to:  ati

---

### Post by dfpd62 on 2007-07-16
Hi

Fiesty has this wonderful feature that allows two or more Xsessions at once, but it appears that only the first login vt06 (ctrl+alt+f7) is allowed access to direct rendering.
so logging in as the first user gets the resources.  this answers other questions i have had too.
Thanks for telling me where to look.

Regards

Donald

---

