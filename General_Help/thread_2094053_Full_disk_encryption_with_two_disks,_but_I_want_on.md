---
title: "Full disk encryption with two disks, but I want one password prompt"
date: 2012-12-12
forum: General Help
---

### Post by bikehead on 2012-12-12
I installed Ubuntu 12.10 with full disk encryption with a passphrase.  Later I added another disk and set it up for full encryption with the same passphrase and added it as a physical volume to my LVM setup.  It works fine, but at boot it prompts me twice for the password, presumably for each disk.  How can I get the boot sequence to try/use the same passphrase for both disks?

I don't mind hacking the bootscripts, but I'm not even sure where the passphrase prompting is done.  Any advice or information on where to look would be greatly appreciated.

-bike

---

