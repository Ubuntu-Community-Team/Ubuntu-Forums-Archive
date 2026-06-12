---
title: "[SOLVED] Dual boot Ubuntu-Windows XP with GRUB"
date: 2008-02-06
forum: General Help
---

### Post by SurrealWraith on 2008-02-06
So, I have my Windows XP all set up and configured on two 250gig hard drives set up in a RAID 0 array, and Ubuntu 7.10 on a separate 250gig hard drive.  If left untouched during the boot process, I will get a GRUB error or an NTLDR error, because both boot loaders seem to be trying to work at the same time.  My question is, how do I go about setting up GRUB as the main boot manager, while maintaining Windows XP as the master operating system for my box?  And furthermore, is it possible to do so without tampering with my Window's hard drives?

---

### Post by upthelum on 2008-02-06
See if [_this_]("http://supergrub.forjamari.linex.org/") is any help. Hopefully someone will offer a quicker fix.

---

### Post by SurrealWraith on 2008-02-06
Is Super Grub different to the GRUB boot manager I installed from the live boot CD?

---

### Post by upthelum on 2008-02-06
> **SurrealWraith said:**
> Is Super Grub different to the GRUB boot manager I installed from the live boot CD?

Sorry i don't know the answer to that. Supergrub was highly recommended to me though in the past. Put supergrub on disc and you can boot it and it will guide you through setting up grub.

---

### Post by SurrealWraith on 2008-02-06
Okay, thanks.  I'll try it right now.

---

### Post by SurrealWraith on 2008-02-12
So, I have come to understand that I can only use a boot-loader such as GRUB to boot multiple OS's when said operating systems are all installed on separate partitions of the same hard drive.  In my case however, each operating system has its own hard drive, so I am told the boot loader will not work.  Since it is much simpler to press F8 to initiate the Bios boot menu and choose the hard drive I wish to boot from than to continue seeking for a way to use a real boot manager, I have decided to do just that.  Thanks for your help.

---

### Post by upthelum on 2008-02-12
Hopefully you'll find a better solution...

---

