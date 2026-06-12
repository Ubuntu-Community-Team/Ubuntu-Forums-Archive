---
title: "Boot problems"
date: 2008-03-13
forum: General Help
---

### Post by colin2006 on 2008-03-13
I successfully installed unbuntu to external hard to use it in my lapto After removing the exerternal drive I attempted to use my desktop vista pc. Howeveri get an error message saying trying to load grub then an erroe number. When I reconect the external drive it gives me a boot menu I chose vista and the pc boots Ok Help

---

### Post by kuja on 2008-03-13
Sounds like the MBR of your internal hard drive is telling it to look for grub on the external hard drive. What you really *need* to get done is to make room on your internal hard drive, and move the boot partition to there, reconfigure grub and your /etc/fstab to reflect the changes. That or live with having to have your external connected because the boot loader is on the external drive.

There may be another option - you may be able to run fixmbr from vista's recovery console to have vista overwrite the boot record, but unless your bios is able to boot from an external hard drive, you won't be able to boot into ubuntu anymore. 

I think you can see where this is going.

---

