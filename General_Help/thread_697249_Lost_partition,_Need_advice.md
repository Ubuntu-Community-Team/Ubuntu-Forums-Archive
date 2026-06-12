---
title: "Lost partition, Need advice"
date: 2008-02-14
forum: General Help
---

### Post by oni-kun on 2008-02-14
This is gonna sound weird lol, okay.. first of all.

I had Windows XP and Ubuntu dual-booting fine together, and for some reason I wanted to try Fedora, So I temporarily replaced Ubuntu with it. Everything went fine, GRUB was replaced with,  well, a more simpler boot menu. I couldn't access Ubuntu without modifying the grub file, and I was lazy so left it. Now the odd part.

I overclocked my processor over its limit, and for some reason in windows, it crashed during a stress test and could not start up! POST worked fine, but the BIOS settings failed to fix anything, windows stated "could not log into C:/windows/system32" bla bla, and Fedora couldn't be found anywhere, now, it totally stopped and nothing worked, but then out of the blue, the fedora DVD worked and I reinstalled fedora into another partition, I backed up everything from my windows partition since I needed to wipe it, cause the XP install CD didn't work without it gone for some reason, Gparted didn't work since something was sucking up 90% of my ram, so I couldn't do much there, so made it messier, installed a 3RD Fedora partition, just to use the DVD's partition manager, I had to install it anyway I think so I just put it into a 500mb partition. I reinstalled windows, and Ubuntu. But I need to access my 2nd Fedora partition, and it says "Unknown Filesystem", and cannot be found. 

so basically

Windows -
Ubuntu -
Fedora -
----
-broken
----
Fedora <-- that one has my backups on it! 
Fedora (dummy one to delete my ntfs partition)
---
Windows
Ubuntu

Any way I can recover that partition? even if it fails to read anywhere else?
-Thanks

EDIT: The partition I want recovered is /dev/sda3, it says "Filesystem: Unknown - flags --lvm"

---

### Post by farruinn on 2008-02-14
> **oni-kun said:**
>  it says "Unknown Filesystem", and cannot be found.

What is "it"? Ubuntu? Fedora? A livecd/install cd?

I would attempt to recover the data with a livecd, but I'm not sure I follow everything you said correctly. Are you sure you didn't overwrite the partition you had your "backup" on?

I'll be honest, I wouldn't trust just a separate partition on my hard drive as my "backup". I think after this you will agree? :)

Good luck

---

### Post by oui on 2008-02-15
bonjour

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

salut

---

