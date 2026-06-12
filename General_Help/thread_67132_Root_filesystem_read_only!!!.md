---
title: "Root filesystem read only!!!"
date: 2005-09-19
forum: General Help
---

### Post by Cud on 2005-09-19
Hi folks... I hope this is the right category, there wasn`t one for "Total Dork Manuvers"
I cant boot linux cause I get a message that dev/hda is mounted read only and then that I should remount it read/write which would be great except that the I thought SU password and root password were the same thing but when I type in my SU password it says LOGIN INCORRECT and then I am left with the only option of rebooting with ctrl-D. I got my self into this mess when I was trying to improve hdrive performance and I
1 Changed the dma mode from udma3 to udma9
2-set 32-bit IO_SUPPORT (# hdparm -c1 /dev/hda)
3-unmasked irc support (# hdparm -u1 /dev/hda)
4- Set multsect to max of 16

So I was in way over my head and then .. mozilla started acting wierd.
I rebooted thinking that all the hdparm changes wouldn`t take effect.
Grub is OK.
Is there anyway out of this mess or should I chalk it up to character building?
Thanks, Jess

---

