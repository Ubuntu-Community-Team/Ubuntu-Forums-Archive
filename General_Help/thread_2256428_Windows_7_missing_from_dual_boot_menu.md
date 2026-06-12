---
title: "Windows 7 missing from dual boot menu"
date: 2014-12-12
forum: General Help
---

### Post by Hvidemose on 2014-12-12
I just installed Ubuntu 14.04 alongside Windows 7, using Dual Boot, like I always do. But this time Windows 7 I absent from the Dual Boot menu.
I tried updating the grub from terminal, and used the boot reparation, but no luck...

Does any body know how I can get Windows 7 in to the start up menu?

---

### Post by Mark Phelps on 2014-12-12
It generally works better here if you tell us exactly what you did, instead of vague remarks like > I tried updating the grub from terminal

If you did "sudo update-grub" in the terminal, then tell us that; otherwise, you risk having us tell you to do things you've already done.

And what is the "boot reparation" stuff? Does that mean you ran "boot-repair"?

---

### Post by Hvidemose on 2014-12-12
Yes, sorry.

I did the "sudo update-grub", and I tried "boot-repair" (bad translation).

The thing is, that the windows partition is there, and i can access it from Ubuntu. The windows 7 is on the partition 2 (sda 2), and Ubuntu on partition 3 (sda 3).

---

### Post by oldfred on 2014-12-12
Post link to summary report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But grub really only boots working Windows, so you may need your Windows repairCD to fix Windows. Boot-Repair can only fix very minor issues with Windows.

---

