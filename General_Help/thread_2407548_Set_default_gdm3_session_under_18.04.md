---
title: "Set default gdm3 session under 18.04"
date: 2018-12-05
forum: General Help
---

### Post by allcoms on 2018-12-05
I have tried several supposed solutions but had no success in getting gdm3 to load MATE (or anything other than GNOME) as the default session under 18.04 so I ended up switching to lightdm.

However, we use powerbroker identity services for AD auth and lightdm has probs with PBIS. I usually can't login first attempt and lightdm crashes after it does let me login so I'd rather use gdm3 if I can get it to login to MATE by default.

Does anyone know how to select the default session for gdm3 under 18.04?

---

### Post by Xian on 2018-12-05
The default session for gdm3 is which ever you last selected. For example if you choose Gnome as the desktop you want ...  the subsequent login will have Gnome as the default. Are you saying that if you choose to load the MATE desktop at the gdm3 login and then reboot & login that gdm3 will automatically load Gnome instead of MATE?

---

### Post by allcoms on 2018-12-06
Hi Xian

Yes, gdm3 always reverts to GNOME as the default session, regardless of what I last logged into. I've just re-installed gdm to check that is still the case.

EDIT

I have opened a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1807197](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1807197)

---

