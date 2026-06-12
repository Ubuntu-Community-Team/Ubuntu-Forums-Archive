---
title: "Truecrypt on XP partition?"
date: 2008-02-07
forum: General Help
---

### Post by PiGeek31415 on 2008-02-07
Now that Truecrypt supports full-disk encryption for windows drives, I'm looking at using it to encrypt my XP drive. 

As of now, I've installed two hard disks in my computer:
- the master drive, running windows, currently unencrypted
- the slave drive, running 7.10, fully encrypted using the gutsy alternate install CD

When I run the encryption tool on windows, it tells me that I need to move GRUB in order for the truecrypt bootloader to be installed to the MBR.

I've googled around, but i can't seem to find any advice on how to accomplish this (and not risk losing all of the data on my encrypted linux disk).

As I understand it, one of the decryption keys is stored in the boot partition, so I'm really afraid of overwriting that by mistake.

Anyone have any suggestions as to what to do?

Thanks,
-PiGeek31415

P.S. - I do have enough external storage to back up the linux drive, if need be. Before messing with bootloaders, is it a good idea to look into backing it up?

---

