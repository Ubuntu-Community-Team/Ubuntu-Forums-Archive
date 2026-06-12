---
title: "Dual booted with windows. GRUB has disappeared and now booting straight to windows."
date: 2015-02-05
forum: General Help
---

### Post by shaneomahony22 on 2015-02-05
Hey Guys,

Im quite new to Ubuntu and dual booting, but i did it a couple months back and it has worked perfectly ever since. Until yesterday when i went to boot into ubuntu like every other day when i discovered the GRUB menu was gone and it just booted straight through to windows. Im now unable to access ubuntu at all.

As i said above, im quite new to this whole area, so any help would be much appropriated. 

Thank you.

---

### Post by oldfred on 2015-02-05
Then it sounds like a Windows update reinstalled the Windows boot loader to the MBR?
Or is this a new UEFI system. Windows resets itself regularly to be first in boot order.

Post link to Summary report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mopar1973Man on 2015-02-05
Old Fred is right just follow the link and run the program. I had to create a dual boot on a friends computer and Ubuntu was already present. So after installing Windows it destroyed "Grub" and did just like you said. Boots right to Windows. Now running that Boot Repair program will rebuild "Grub" and it work again as usual.

---

