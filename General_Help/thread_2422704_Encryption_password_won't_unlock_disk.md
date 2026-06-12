---
title: "Encryption password won't unlock disk"
date: 2019-07-11
forum: General Help
---

### Post by and1122 on 2019-07-11
Hi! I don't know if this happens to everyone, I'm running Ubuntu 19.04 and I enabled disk encryption, however, I noticed that if I enter a wrong password on the first try, it won't unlock the drive even when I enter the right password on the second try, not matter what if I enter the wrong password I get stuck and can't unlock my computer, it just shows a message saying something like: encryption failed bad password or options. The current workaround is forcing a shutdown by long pressing the power button and trying again, however, I don't know if this is something that is supposed to happen or if it's just my laptop or if I should report it as a bug. Just to make sure, I tried it several times and it's always the same result. If anyone knows how to fix this or knows why this happens, please let me know. Also I don't know if force shutting down my computer could do any damage, considering that my drive is encrypted I don't know if data could be lost by doing that.
Thank you in advance!

---

### Post by TheFu on 2019-07-12
First, pre-boot, there is little chance that forced power off will corrupt the storage, so I would relax.  The boot files are only written (opened in write mode) as part of a kernel upgrade or forced initrd rebuild.  At boot time, those files should all be opened read-only.

I use OS partition encryption too, but combine a passphrase with a 2FA key to have a very long total passphrase - think it is about 50 characters.

Anyway, how many times should a bad passphrase be allowed?   Seems that forcing a hard reboot would be a security feature, yes?  My next expected reboot/shutdown is Sunday - I'll see what happens then.

---

