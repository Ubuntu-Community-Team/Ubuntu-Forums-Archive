---
title: "Cloning/Backup LUKS volume"
date: 2008-06-04
forum: General Help
---

### Post by wiz561 on 2008-06-04
Hi!

I encrypted the hard drive when I installed Ubuntu 8.04.  I used the alternate CD, created an encrypted partition first, then created a volume group on that encrypted partition for / and /swap.  The /boot is unencrypted.

The question I have is how does one go about backing up the volume?  My goal is to 'clone' the ubuntu installation so I can deploy that image to multiple machines.  I attempted to use clonezilla...which did work alright, but when I booted up into Ubuntu, it gave an error about a drive-mapper.

So now, what I have done is cloning just the sda5 partition, which is encrypted.  Clonezilla is using dd to do the backup, but is there a better way to do this?  Better, meaning more efficient?  

The other gotcha is that this is a dual-boot system and the windows partition is full encrypted with PGP.  So, first it boots to the PGP splash screen, you enter your PGP password.  Then it loads grub.  From there, you can choose Windows or Ubuntu.  Yes, complicated...but I got it working on the one box.  Now I just have to clone it.  :)

Thanks,
Mike

---

### Post by vcrpcant on 2010-12-22
I'm also interested on this matter.

I've cloned an ubuntu 10.04 encrypted LVM with clonezilla and the original disk boots fine, but the others (on some motherboards only) give me an error: "ELF header smaller than expected".

This error doesn't happen when cloning to an equal hard drive (same maker, model and size).

Anyone knows what's happening and how to solve this?

---

