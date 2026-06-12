---
title: "Unreliable boot up"
date: 2013-12-22
forum: General Help
---

### Post by Dr Cod on 2013-12-22
Hi,
I'm running Ubuntu 13.10, dual-booted with Windows 8.1 on a Lenovo IdeaPad. I installed Ubuntu in February 2013 and had real trouble with the installation thanks to the hated secure boot thing. Since installation, I am able to boot into both Windows and Ubuntu but booting into Ubuntu has always been unreliable. When I select Ubuntu from the GRUB menu sometimes it boots and sometimes it doesn't. When it does boot, it takes a long time for anything to happen. When it doesn't, the computer just sits there with a blank screen and I have to power off and try again. This can happen several times in a row.

I have been putting up with this for months now, but as I now have a few days off I have decided to try and fix it. I am not a confident or knowledgable computer guy. I ran boot repair and got this message:

'The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))'

And I also got this URl with more info:

[http://paste.ubuntu.com/6616790/](http://paste.ubuntu.com/6616790/)

I don't know if the information from boot repair is the cause of my booting problems. I don't really know how to interpret what it says.

Can anyone help?

Thanks

---

### Post by grahammechanical on 2013-12-22
Secure boot is not really the issue. Ubuntu 13.10 has a signed kernel that will install on a motherboard that has Secure Boot activated. From reading posts on this forum I would say that UEFI and not having a small partition at the start of the hard disk where both Windows 8 and Linux can put some boot information is the issue. I most certainly do not know what I am talking about on this matter. :)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See the section called Creating an EFI partition. I think that Boot Repair is pointing you in the right direction. Others, more knowledgeable in this subject than me will offer better advice. 

Regards

---

