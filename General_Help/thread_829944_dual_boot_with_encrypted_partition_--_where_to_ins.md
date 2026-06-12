---
title: "dual boot with encrypted partition -- where to install grub"
date: 2008-06-15
forum: General Help
---

### Post by melopsittacus on 2008-06-15
Hi, I have the following partition scheme on my first hard disk:

1. primary partition -- Windows
2. primary partition -- Linux boot (unencrypted)

logical partition: volume group for encrypted volumes, containing
 - swap partition
 - root partition


Now the question is: on which of these should I install GRUB and which one should I make bootable (i.e. set the bootable flag)?

During installation process the installer did not let me put it on the boot partition (2. primary). I do not want it to be in the MBR either, because I am planning to encrypt the Windows partition as well with Truecrypt, and then it installs its own bootloader there.

---

### Post by popsgone on 2008-06-15
Just a thought, I would leave the Windows partition as Active (Windows/Dos). Linux does not require this. From Windows download a free boot load manager and install it. If you using Vista I suggest BCD 1.72. Just google it to find it. Or you could just install Ubuntu through Windows and it is created for you. By the way, if you're not familiar with the Computer Manager under Windows it can be a REAL PAIN.....

---

### Post by melopsittacus on 2008-06-15
Thanks for the suggestion, but I am not sure BCD would help me :(
(btw. I assume you meant easyBCD 1.7.2)


First of all, I have XP, not Vista. I have seen in the docs that it supports Vista as well, but it seems to me that it needs Vista's booting mechanism to work, so it's not possible to use without Vista.

Second, it does not mention that it supports encrypted file systems, so I assume it does not.

And third, this boot manager again would be installed to the MBR, and get overwritten by Truecrypt as soon as I encrypt the Windows partition.

So the question is still: where do I have to put GRUB.

And another question: is the partition with the bootable flag set the same as the active partition?

---

