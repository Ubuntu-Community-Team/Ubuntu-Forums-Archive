---
title: "Partition encryption for a dual boot laptop"
date: 2008-02-19
forum: General Help
---

### Post by MrPage on 2008-02-19
I would like to encrypt my whole laptop (so using two drives is not possible) but I have some concerns.

my partition table is as follows.

sda1 - dell (I don't need/want to encrypt this, nor do I wish to lose it)
sda2 - windows xp
sda3 - /
sda5 - swap
sda6 - general storage (formatted ext3 - xp has an ext2fs driver so it can use it too)

My whole dilema could be subverted if there were a whole-disk encryption scheme that both linux and windows kernels natively supported - but as far as I can tell there is no such thing.
OR if linux supported the kind of home & swap encryption that Mac OS X supports - I'd be golden - but I'd problably also have to upgrade XP to Vista Ulitmate and start using BitLocker...which I know nothing about....

so here's what I'm thinking - please tell me if I'm wrong.

-I should reinstall Ubuntu using alternate cd LVM encryption for / and swap.  I've never done this before and I hope that it optionally can be limited to just the partition you're installing to and not the whole drive.

-I should then use something like Free Compusec to encrypt XP.  Steve Gibson says it will work on-the-fly while using Windows but I'm not sure if that will limit itself to just the windows partition or try to do the whole drive (very bad for linux).

-I should then use something like truecrypt on my general storage - since both linux and windows will be able to open that container.  As of right now Truecrypt 5.0a is available, and the linux version doesn't support formatting the container Ext3 (BOOOO!!!!) so there goes all of my 4GB+ files I have (DVD ISOs and virtual machines) unless I submit to some NTFS abuse.

What do you think?


One think I Really want to avoid is typing in a password several times at boot up.  I heard if you have your home and swap encrypted then you have to unlock each one separately...that's dumb...
Although I don't mind doing one for the boot, and one for the truecrypt container.

Thanks for your time
~MrPage

---

### Post by sunbird on 2008-03-25
I'm in a similar situation on a dual-boot Macbook Pro (OS X / Ubuntu 7.10). Did you ever get any responses? From poking around, I think you have to do the whole drive if you use the alternate installer cd... but I have not confirmed this myself. I'd like to do the ubuntu partition and swap, don't care about os x as i plan to delete that partition eventually anyway.

Did you ever find a solution?

---

### Post by MrPage on 2008-07-23
No, I never found any good solution to that problem.

What I wound up doing was just formatting the whole drive using the alternate cd and whole-drive encryption (like you mentioned there).  I no longer have a windows partition.  I just use a virtual machine for that crap.

---

