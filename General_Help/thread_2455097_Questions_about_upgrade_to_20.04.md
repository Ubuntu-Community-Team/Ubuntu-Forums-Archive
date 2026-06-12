---
title: "Questions about upgrade to 20.04"
date: 2020-12-12
forum: General Help
---

### Post by Old Jimma on 2020-12-12
Hi Ubuntuers:

I want to upgrade to 20.04 and have concerns:

[LIST]
[*]I've got several hard drives. will the fstab be preserved
[*]what happens to my crontab file?
[*]
[/LIST]

I'll be grateful if some one can address these!

Old

---

### Post by TheFu on 2020-12-12
Make a backup with everything you cannot lose, then try it. See how it goes on your hardware.
Hint: I'd definitely backup the crontab and fstab files if you don't want to lose those.

Any OS upgrade/migration is like open heart surgery.  Always have a heart bypass machine ready since every once in a while bad things happen.

---

### Post by Old Jimma on 2020-12-12
Thanks again, Fu!

Old

---

### Post by Dennis N on 2020-12-12
Based on my experience over many in-place upgrades, expect: The fstab file will not be changed. Things in your home folder will not be changed - that includes firefox settings and bookmarks and the other application and system settings stored there. That probably includes crontab, but I have not used that for anything for some time.

The gnome-shell extensions will not upgrade. You have to do that afterwards. You should disable these before upgrading.

I only do one-step upgrades to the next 6-month release - no LTS to LTS upgrades, which intuitively seem riskier.

---

### Post by mrdc76 on 2020-12-12
Remember to purge all PPAs if you have added any.

---

### Post by Old Jimma on 2020-12-12
Hi mrdc76:

Thanks for your reply!

I'll certainly do that, but why disable them?

Tx again,
Old

---

### Post by CelticWarrior on 2020-12-12
There's no need to purge the PPAs or even - theoretically - disable them.
The installer is supposed to disable them anyway but sometimes things don't go as planned. And disabling the PPAs before starting the release upgrade makes it faster, albeit only slightly.

In summary, the closest the system is to a pristine installation, without third-party software sources the better the chances of a successful upgrade.

---

### Post by Old Jimma on 2020-12-12
Thanks Celtic,

What you wrote makes sense.

Thanks!

---

