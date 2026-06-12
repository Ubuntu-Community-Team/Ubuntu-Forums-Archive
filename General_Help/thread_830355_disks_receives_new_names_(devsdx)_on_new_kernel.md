---
title: "disks receives new names (/dev/sdx) on new kernel"
date: 2008-06-15
forum: General Help
---

### Post by daffy_ on 2008-06-15
Hi,

when I run my ubuntu 8.04 64 bit server on kernel 2.6.24.26-server everything behaves as it should. If I, on the other hand, boots it with 2.6.24-18-server (or 2.6.24-17) the disks receive wrong names.

For instance, /dev/sda becomes /dev/sdb, /dev/sdb becomes /dev/sde, etc. (So my fstab is completely wrong when running on kernels > 2.6.24-16.)

This, of course, wreaks havoc in my setup/fstab. And, in addition, is not at all what I should have according to my motherboard and how I have attached the disks there.

My MoBo is a ASUS M3A-H, AMD 780G chipset.

And when I run 2.6.24-16 kernel, the disks are found as I expected them to be, according to what I see in the BIOS and according to how I have attached them to the MoBo. When I run kernels > 2.6.24-16, I can't see any specific pattern which explains what happens, I've not seen a pattern which can tell me what sequence the disks are named in, and why they receive a different sequencing than when running on 2.6.14-16.

Hope someone has seen this problem before and knows how to solve it! :)

---

### Post by lswb on 2008-06-15
Can you rewrite your fstab so all disks are mounted by uuid? It won't solve the problem of why the disks are ordered differently with the different kernels, but it will make that irrelevant. Also see if you have any lines beginning with "map" in /boot/grub/menu.lst

---

### Post by daffy_ on 2008-06-17
Thanks for the tip, I'll definitely look into that (I wasn't aware that was possible). It will hopefully solve my problem, but it still keeps me puzzled to why this happens... :(

---

### Post by daffy_ on 2008-06-25
It worked with UUID, thanks for the tip! :) But, when I upgraded to 2.6.19, the sequence the disks were named was correct again. Now I have learned the uuid trick and will be using that in the future. :)

---

