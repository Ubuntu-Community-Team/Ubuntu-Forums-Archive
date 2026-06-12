---
title: "Upgrading via Alternate CD method never finishes!"
date: 2008-04-27
forum: General Help
---

### Post by cookies on 2008-04-27
I'm trying to upgrade with the method of the Alternate CD described here:
[https://help.ubuntu.com/community/HardyUpgrades/Kubuntu](https://help.ubuntu.com/community/HardyUpgrades/Kubuntu)

And at "Getting New Packages" it always reaches 3888 packages then jumps down to 3079. This upate has been interrupted by closing the window. I dunno if that has anything to do with it. Also, disc activity always slows at 3434 packages before picking up again.

Is there anyway to make it complete, I've tried upgrading with just the internet, but it always tells me to use the CD....

Help, please.

EDIT:
Oh at last some error!:
```

Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/pool/main/t/ttf-arphic-ukai/ttf-arphic-ukai_0.2.20080216.1-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.2.20080216.1-0ubuntu1_all.deb Hash Sum mismatch
```

So it fails on some fecking fonts! GAH!!!

---

### Post by cookies on 2008-04-28
El bump-o. Help-o please.

---

### Post by cookies on 2008-04-29
.... Hmph. I'll file a bug. And, maybe install openSUSE. :/

---

### Post by Rainstride on 2008-04-29
bad burn? have you run the "check disk for errors" in the menu where you install from?

---

### Post by cookies on 2008-04-29
> **Rainstride said:**
> bad burn? have you run the "check disk for errors" in the menu where you install from?

Yes, the disc was fine. I suspect the iso contains mismatched files and sums. (I tried 2 discs)

---

### Post by Rainstride on 2008-04-29
where you trying to do the encrypted install?

---

### Post by cookies on 2008-04-29
> **Rainstride said:**
> where you trying to do the encrypted install?

No. I was doing the CD method because my DSL speed is failurifically slow.

---

### Post by Rainstride on 2008-04-29
oh, just noticed the link. are you doing this inside ubuntu or restarting to load the disk? if you restart theres an option on the disk that says upgrade from disk(on ubuntu anyway)

---

### Post by cookies on 2008-04-29
> **Rainstride said:**
> oh, just noticed the link. are you doing this inside ubuntu or restarting to load the disk? if you restart theres an option on the disk that says upgrade from disk(on ubuntu anyway)

Inside Ubuntu. It's the alternate cd, so I'll have to dig through text to find "upgrade".

---

