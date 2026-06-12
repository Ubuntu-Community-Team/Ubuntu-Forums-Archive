---
title: "libpam and libparted causing issues with disk recognition"
date: 2006-12-22
forum: General Help
---

### Post by Koobi on 2006-12-22
Hi guys,
I've been using since it's first version. Right now I'm on 6.06 and I upgraded the system after a very long time, the other day.

I noticed that one of the upgrades involved libparted and libpam.

After the upgrade, the PC wasn't rebooted for an entire day but it worked fine.

After rebooting, I recieved a bunch of errors mentioning orphan inodes I believe. At this point I was asked to either manually repair the system as root or to hit Ctrl + D to ignore the issue. Ctrl + D took me along a bit and then my system froze before X was even started.

I then tried to manually repair. fsck didn't solve anything.

I have a feeling this has to do with the upgrade. I can go into recovery mode via GRUB but I can't do much there since apt is unavailable.



I could just boot through the Live CD, mouth my partitions, write my important data to a CD/DVD and reinstall the entire thing...but unfortunately, I don't have as much time as I'd like.

Is there anyway I could repair the system? I'm guessing that if I could uninstall libparted and libpam or perhaps repair them (can my file system be recognized without those two libs?) but how would I do this if I can't access apt?


Thanks for your time :)

---

