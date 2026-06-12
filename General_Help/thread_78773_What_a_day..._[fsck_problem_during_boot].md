---
title: "What a day... [fsck problem during boot]"
date: 2005-10-18
forum: General Help
---

### Post by mjwood0 on 2005-10-18
So I decide it's time to take the leap to Breezy.  Try to boot my laptop to the Hoary partition with no network card in the PCMCIA slot.  No problem, I'll just insert the card after boot.  Of course, ntp fails during boot since it can't connect to the time server.   No biggie, right?

So, I boot, insert my network card and start getting errors from sendmail.  Something about the mailbox mounted readonly and can't write to it.  So I decide to bring down my whole system and reboot with the network card in.

Reboot goes fine, hangs on trying to shutdown Laptop Support.  Hangs hard.  Weird since it's never done this before.  So I cringe and hard powercycle the laptop.

Reboot and get errors on my / (root) partition.  Drops me out of the install and tells me to run fsck manually after remounting the root partition rw. 

Mind you, I'm using EXT3 on all my drives.  I type in the fsck -p /dev/hda5 (my root partition) and it asks me if I really want to do this as it could cause damage to my EXT3 partition.  I say no and it re-reads the journal and claims all's well.

So... I reboot and get the same error on my / (root) partition.  I don't want to run fsck and ruin anything so what do I do?

Sorry this is long winded.  I was excited about installing breezy tonight and now I've got this problem..

MJWood0

---

### Post by mjwood0 on 2005-10-18
Ahh well... I guess it's a sign to install Breezy...  

Life always looks better after a nice dinner with the family.

MJWood0

---

