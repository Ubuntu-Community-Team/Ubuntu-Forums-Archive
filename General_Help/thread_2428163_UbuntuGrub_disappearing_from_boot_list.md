---
title: "Ubuntu/Grub disappearing from boot list"
date: 2019-09-30
forum: General Help
---

### Post by Frank67 on 2019-09-30
I've been dual booting Ubuntu 18.04 and Windows 10 (for a few months), recently my laptop (Acer Predator G9-791) started booting directly to Windows, and doesn't show anything else in the boot menu. 

I ran boot-repair, which didn't seem to change anything (log: [http://paste.ubuntu.com/p/c6fyCQCtkJ/](http://paste.ubuntu.com/p/c6fyCQCtkJ/)).

Using efibootmgr (from a live cd) showed "ubuntu" as a boot entry, but not in the boot order. I added it to the boot order, which also didn't change anything, and it was no longer in the boot order upon booting back into the live cd and examining the boot order again.

Any help would be appreciated, I'm in over my head here.

---

### Post by westie457 on 2019-09-30
No real ideas from here, just a couple of things to check.

1) From within Windows check that 'Fast Startup' has not been turned on.

2) In the Bios pages reset 'Trust' on the Ubuntu Boot Files

If the issue is not fixed at least it has removed some of the more obvious reasons.

---

### Post by Frank67 on 2019-09-30
I love it when the first thing someone thinks of solves my problem! Adding the Ubuntu boot files as trusted put them on the list and everything boots fine now. Thanks so much.

---

