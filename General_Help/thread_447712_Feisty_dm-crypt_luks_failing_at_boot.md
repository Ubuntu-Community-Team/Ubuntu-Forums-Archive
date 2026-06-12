---
title: "Feisty dm-crypt luks failing at boot"
date: 2007-05-18
forum: General Help
---

### Post by thebasard on 2007-05-18
Folks,
I'm hoping someone here can help me.  I'm running Feisty and I've created an encrypted disk on /dev/sda3 using cryptsetup and luks as described in one of the how-to posts in this forum.  The whole process goes well until I reboot.

At each reboot, I'm prompted for my passphrase twice and 50% of the time or more the /dev/mapper/sda3 device is not found and thus fails to get mounted.  My passphrase is accepted though.

---

### Post by secure bit on 2007-12-13
I think LUKS need some better support, I believe it is a great project but it is that lack of support !

---

