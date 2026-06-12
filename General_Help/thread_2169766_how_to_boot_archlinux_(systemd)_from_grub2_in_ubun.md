---
title: "how to boot archlinux (systemd) from grub2 in ubuntu ?"
date: 2013-08-23
forum: General Help
---

### Post by zebul on 2013-08-23
When I try to boot archlinux (which uses systemd) I got a kernel panic with an error. What configuration must I do so that grub2 installed with ubuntu (12.04) could correctly boots archlinux?
Note that archlinux boots fine when I use the grub (legacy) used by archlinux and the proper configuration (tells via menu.lst to use init=/usr/lib/systemd/systemd)

---

### Post by oldfred on 2013-08-23
Post link to BootInfo report so we can see details. I have not booted Arch.

 If using grub legacy(?) you can always install it to a PBR - partition boot sector and chain load from grub2. Grub legacy does not complain about installs to a PBR like grub2 does.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

The last time I used grub legacy was with 9.04, but I had chain load entries back to it from grub2 like this. But grub2's boot loader was in the MBR of hd2.


 menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

IF booting partition:


 menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

---

