---
title: "Encrypting Home folder in dual boot"
date: 2021-08-12
forum: General Help
---

### Post by Gordonbp531 on 2021-08-12
Ubuntu 20.04 dual boot with Windows 10. (Ubuntu is my default OS).
Is there any way to retrospectively encrypt my Home folder, and if so will that impact on the dual boot at all?

---

### Post by TheFu on 2021-08-12
**any** way?  Sure.
Is it easy?  That depends on your skill level.

Directory level encryption was removed from Ubuntu for a number of reasons - performance and poor security were the main reasons, but migrations and upgrades were problems too.

If you want to encrypt the entire /home partition, assuming /home is on a dedicated partition, then things are a little harder, but much more secure.  In general, if any part of a system isn't encrypted, then the entire system is at risk and encrypting just a small part is sufficient for little brothers, not people who are serious about gaining access and have google skills.

Another option is NOT to encrypt your HOME, but to encrypt an external device, then dynamically decrypt it and have symbolic links so it appears to be under your HOME, but really isn't. Lots of people here do that for their documents  They have ~/Documents ----> /media/myname/docs which is a different storage device, mounted under /media.  The security issues with encryption still exist in this situation, but if it is a portable device, say a flash drive, then you can take it out when you aren't watching the computer. That will mitigate some issues.  [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it) explains. He makes videos too.

Whenever using encryption, be 100% certain you have excellent backups.  The fix for most issues on encrypted storage is to wipe it all and start over, restoring the backups.

---

