---
title: "gparted question"
date: 2006-10-29
forum: General Help
---

### Post by toastedcheese on 2006-10-29
I'm trying to use gparted to enlarge my /boot partition and am running into some (probably easily fixed) problems.

The gparted documentation seems to say that I need to unmount a partition to resize it. Whenever I try to do this through gparted, though, I get a message  along these lines:

"Could not unmount /dev/hda7

umount: /: device is busy
umount: /: device is busy."

So, what am I doing wrong? Note that I am in the middle of an upgrade from Breezy to Dapper (working my way up to Edgy!) so things are untidy on my computer, but this particular error is puzzling.

---

### Post by meng on 2006-10-29
I'd say it's safest to run the Ubuntu LiveCD or else the GParted LiveCD to resize partitions, so that nothing on your hard drive is mounted at the time of the resizing operations.

I'm not 100% sure of that error message you're getting, but it seems to suggest that you're trying to unmount your root partition (/) which of course you can't do!

---

### Post by toastedcheese on 2006-10-29
That makes sense. Is there a way to resize in gparted without a LiveCD, though? I'd just rather not reboot my computer when I'm in the middle of an upgrade.

---

### Post by meng on 2006-10-29
Ah I didn't read that bit. That seems pretty tricky, you'll want to get advice from someone cleverer than I.

---

### Post by Boelcke on 2006-10-29
Er, that upgrading thing can be tricky.  The few upgrades I've done (one) hasn't been without any hitches.  I'd have to recommend getting your upgrade done first, then try messing around with partitions -- not during!

Remember, though I've had great luck with gparted, and messing around with partitions, it's a risky business.  That "backup first" advice is pretty serious stuff when messing with partitions.

I ended up using the gparted boot-cd to juggle mine around, just before upping from Breezy to Dapper.

---

### Post by toastedcheese on 2006-10-29
Re: waiting to resize until the upgrade is done, that would be wise advise if the upgrade wasn't the reason I need to enlarge my boot partition. I'm running into errors and I'm pretty sure it's because /boot has run out of room (again.) I definitely should have checked this before I began upgrading, but I stupidly forgot.

If there's no safe way to resize without a LiveCD, I'll probably just see if I can make space some other way and, worst comes to worst, I'll suck it up and use the LiveCD.

Thank you for the advice so far, though!

---

