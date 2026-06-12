---
title: "Changing grub default"
date: 2014-12-21
forum: General Help
---

### Post by robbie1981 on 2014-12-21
I have a dual boot with win7 64 / ubuntu 14.04.  I installed Xen hypervisor which modified the grub bootloader to boot with Xen as the default which I don't want.  Windows and ubuntu without zen boot ok when selected.  I installed and used "Grub Customizer" and under the general settings tab chaged the default to previously booted entry.  I saved it and selected install to MBR but after several reboots ubuntu with Zen is still the default.  I have found amother way round the issue I was haveing so I don't need zen but would like to have either Windows or Ubuntu as the default.

If any body has been able to solve this please let me know.

Cheers

---

### Post by oldfred on 2014-12-21
Do not know anything about Zen. What little I know I thought you installed under it and it booted first?

But curious about what this may show. I do not think it scans for anything related to Zen, so may not be useful.

         Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

