---
title: "Often Can't Find Additional Storage"
date: 2018-12-12
forum: General Help
---

### Post by SciFiFan on 2018-12-12
On my custom built _desktop_ computer I have a SSD with Ubuntu 16.04 LTS as the primary drive along with an internal hard disk for additional storage. At first boot, the hard disc drives are shown as icons on left panel. During the session, the additional hard drive icon occasionally drops off and can not be accessed until a reboot is done.  Is there anything to be done to ensure the additional drive(s) don't drop off?

This setup has been working for years (May-2016) and while it may have been happening for a long time, I haven't noticed it until recently.

---

### Post by Autodave on 2018-12-12
My first thought is to check connections: one or more may have worked loose.  Next possibility is a HD failing.  Third would be a motherboard failing, but that would be very rare.

---

### Post by SciFiFan on 2018-12-12
Thank you for the reply & thoughts.
The desktop is a SFF (Small Form Factor) with no fan. Internal connections haven't been touched since case screwed back together and unit hasn't moved or table it sits on. 
As I said, it is very intermittent and simply more of an annoyance than anything major.

---

### Post by Impavidus on 2018-12-12
Probably a hardware problem. A connector can work itself loose by vibrations or temperature swings. Open the thing, clean the connectors and put it back together.

Completely unrelated, for an internal hard drive it's easiest if you mount it automatically via fstab. No icon in the left panel, but the drive will be available at whatever mountpoint you chose.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

